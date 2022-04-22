<template>
  <div id="card-serie">
    <!-- carico l'immagine che deve essere visualizzata -->
    <img :src="imgOrError('/w342', serie.poster_path)" :alt="serie.name"> 
    <!-- e la descrizione che spunta con l'hover -->
    <div class="series-description">
        <p><strong>Titolo:</strong> {{serie.name}}</p>
        <p><strong>Titolo originale:</strong> {{serie.original_name}}</p>
        <span><strong>Lingua:</strong> {{serie.original_language}}</span>
        <span><strong>Voto:</strong> {{serie.vote_average}}</span>
    </div>
                  
  </div>
</template>

<script>
export default {
    name: 'SeriesItem',

    data(){
        return {

            // creo un dato che mi serve per caricare le immagini
            defaultImgUrl: 'https://image.tmdb.org/t/p/',


            icoLangPath: './en.png'

        }
    },

    props:{
        serie: Object
    },

    methods:{

        imgOrError(height, imgName){
            
            //creo una costante con il link dell'immagine di errore
            const errorImgPath = 'https://www.salonlfc.com/wp-content/uploads/2018/01/image-not-found-scaled-1150x647.png'

            if(imgName === null){      // se il path della copertina è null
                
                // carica l'immagine di errore
                return errorImgPath

            }
            
            // altrimenti, se il path di copertina ha un valore

            return this.createImagePath(height, imgName) // carica il path della copertina generato con la funzione

        },
        




        // creo una funzione che ritorna il path completo per caricare la copertina
        createImagePath(height, imgName){

            /* 
            l'url di default +
            il parametro di grandezza dell'immagine +
            il path della copertina di ogni serie o film
            */

            const totalPath = this.defaultImgUrl + height + imgName

            // e ritorna il path intero
            return totalPath
        }
    }
}
</script>

<style lang="scss" scoped>

    
    .series-description{
        display: none;
        flex-direction: column;
        padding: 11px;
        font-size: 12px;
        row-gap: 6px;
        p{
            overflow-wrap: break-word;            
        }
        strong{                    
            color: gray;
        }
    }

    #card-serie:hover{
        cursor: pointer;            
        img{
            display: none;
        }
        .series-description{
            display: flex;
            flex-direction: column;
        }
    }
</style>