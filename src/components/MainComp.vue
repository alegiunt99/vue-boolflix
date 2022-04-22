<template>
  <main>
        <!-- creo il container che contiene film e serie tv -->
        <div class="container">

            <!-- creo un container solo per i film -->
            <div class="movies-box">

                    <h1>FILM</h1>

                    <div v-if="films.length > 0" id="movies-container">

                        <!-- creo la card di ogni serie trovata -->

                        <FilmItem class="movies-card"  :film="movie" v-for="movie in films" :key="movie.id"/>

                    </div>
                            
            </div>



                <!-- creo un container per le serie tv -->
            <div class="tv-series-box">

                <h1>SERIE TV</h1>

                <div v-if="tvSeries.length > 0" id="tv-series-container">

                    <!-- creo la card di ogni serie trovata -->
                    
                    <SeriesItem class="series-card" :serie="serie"  v-for="serie in tvSeries" :key="serie.id"/>

                </div>
            </div>
        </div>       
  </main>
</template>

<script>

import FilmItem from '@/components/FilmItem.vue';

import SeriesItem from '@/components/SeriesItem.vue';

export default {
    // metto il nome del componente
    name: 'MainComp',

    // creo i data
    data(){
        return {

            // creo un dato che mi serve per caricare le immagini
            defaultImgUrl: 'https://image.tmdb.org/t/p/',


            icoLangPath: './en.png'

        }
    },

    components:{

        SeriesItem,

        FilmItem

    },

    props: {

        tvSeries: Array,

        films: Array
    },

    /*methods:{

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
            

            const totalPath = this.defaultImgUrl + height + imgName

            // e ritorna il path intero
            return totalPath
        }
    }*/
}
</script>

<style lang="scss" scoped>

    // contenitore generale
    .container{
        max-width: 90%;
        margin: 50px auto;
        display: flex;
        flex-direction: column;
        color: white;

        //*************** FILM ***************
        .movies-box{
            display: flex;
            flex-direction: column;
            #movies-container{
                display: flex;
                flex-wrap: wrap;
                justify-content: space-around;
                margin-top: 30px;
                .movies-card{
                    width: 21%;
                    display: flex;
                    flex-direction: column;
                    row-gap: 2px;
                    justify-content: center;
                    border: 1px solid darkgray;
                    border-radius: 5px;
                    margin-bottom: 20px;
                    margin-left: 2px;
                }
            }
        }

        //*************** SERIE TV ***************
        .tv-series-box{
            display: flex;
            flex-direction: column;
            #tv-series-container{
                display: flex;
                flex-wrap: wrap;
                justify-content: space-around;
                margin-top: 30px;
                .series-card{
                    width: 21%;
                    display: flex;
                    flex-direction: column;
                    row-gap: 2px;
                    justify-content: center;
                    border: 1px solid darkgray;
                    border-radius: 5px;
                    margin-bottom: 20px;
                    margin-left: 2px;
                }
            }
        }

    }

    @media screen and (max-width: 370px) {

        .container{
            .movies-box{
                #movies-container{
                    .movies-card{
                        width: 88%;
                    }
                }
            }
             .tv-series-box{
                #tv-series-container{
                    .series-card{
                        width: 88%;
                    }
                }
            }
        }
        
    }
    
</style>