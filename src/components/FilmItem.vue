<template>
  <div id="card-film">
       <!-- carico l'immagine che deve essere visualizzata -->
        <img :src="imgOrError('/w342', film.poster_path)" :alt="film.title" class="poster-img">

                    <!-- e la descrizione che spunta con l'hover -->
        <div class="movie-description">
            <p><strong>Titolo:</strong> {{film.title}}</p>
            <p><strong>Titolo originale:</strong> {{film.original_title}}</p>
            <span>
                <strong>Voto:</strong>  
                <span v-for="(star, index) in howStarsVote" :key="index" class="stars-vote">
                    <i class="fa-solid fa-star"></i>
                </span>
            </span>
            <p>
                <img v-if="hasImage" @error="imageError($event)" class="flag" :src="require(`@/assets/img/${film.original_language}.png`)" :alt="film.title">
                <span v-else class="language-error"> {{film.original_language}}</span>
            </p>
        </div>   
  </div>
</template>

<script>
export default {
    name: 'FilmItem',

    data(){
        return {

            // creo un dato che mi serve per caricare le immagini
            defaultImgUrl: 'https://image.tmdb.org/t/p/',

            hasError: false,

            aviableFlags: ['en', 'it', 'fr', 'ja', 'es'],

        }
    },

    props:{
        film: Object
    },

    computed:{
        hasImage(){
            return this.aviableFlags.includes(this.film.original_language);
        },

        howStarsVote(){
                
                //let newArray = ['a', 'b', 'c', 'd', 'e'];
                let newArray = [];

                let vote = this.numberVote();
                
                while(newArray.length < vote){
                    
                    newArray.push('x');

                }
                /*while(newArray.length > vote){
                    console.log('dentro');

                    newArray.pop();


                }*/
                
                return newArray;
        },
        
    },

    methods:{

        imgOrError(height, imgName){
            
            //creo una costante con il link dell'immagine di errore
            const errorImgPath = require(`@/assets/err_img.jpg`);

            if(imgName === null){      // se il path della copertina è null
                
                // carica l'immagine di errore
                return errorImgPath;

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
        },

        imageError(event){

            event.target.style.display= 'none';
            this.hasError = true
        },

        

        // per il numero di stelle
        numberVote(){
            
            // creo una variabile che restituisce solo numeri interi
            let vote = Math.floor(this.film.vote_average)+1;

            // creo una condizione
            if(vote < 5){

                //se il voto è inferiore a 5, si lascia normale
                return vote

            }
            
            //altrimenti, se è maggiore o uguale a 5, spunterà comunque 5

            return vote = 5
        },

        
    },

    
}
</script>

<style lang="scss" scoped>
    .poster-img{
        height: 100%;
    }
    .movie-description{
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

        img.flag{
            display: inline-block;
            width: 22px;
        }
    }

    #card-film:hover{
        cursor: pointer;            
        .poster-img{
            display: none;
        }
        .movie-description{
            display: flex;
            flex-direction: column;
        }
    }
    .stars-vote{
        color: yellow;
        margin-right: 3px;
    }
    
</style>