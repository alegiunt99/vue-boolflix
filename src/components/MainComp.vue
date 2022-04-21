<template>
  <main>
      <!-- creo il container che contiene film e serie tv -->
      <div class="container">

          <!-- creo un container solo per i film -->
          <div class="movies-box">

                <h1>FILM</h1>

                <div v-if="films.length > 0" id="movies-container">

                    <!-- creo la card di ogni serie trovata -->
                  <div class="movies-card" v-for="item in films" :key="item.id">

                      <!-- carico l'immagine che deve essere visualizzata -->
                    <img :src="imgOrError('/w342', item.backdrop_path)" :alt="item.title">

                    <!-- e la descrizione che spunta con l'hover -->
                    <div class="movie-description">
                        <p><strong>Titolo:</strong> {{item.title}}</p>
                        <p><strong>Titolo originale:</strong> {{item.original_title}}</p>
                        <span><strong>Lingua:</strong> {{item.original_language}}</span>
                        <span><strong>Voto:</strong> {{item.vote_average}}</span>
                    </div>              
                  </div>
                </div>
              
          </div>
            <!-- creo un container per le serie tv -->
          <div class="tv-series-box">
              <h1>SERIE TV</h1>
              <div v-if="tvSeries.length > 0" id="tv-series-container">
                  
                  <!-- creo la card di ogni serie trovata -->
                <div class="series-card" v-for="item in tvSeries" :key="item.id">

                    <!-- carico l'immagine che deve essere visualizzata -->
                  <img :src="imgOrError('/w342', item.backdrop_path)" :alt="item.name"> 

                    <!-- e la descrizione che spunta con l'hover -->
                  <div class="series-description">
                        <p><strong>Titolo:</strong> {{item.name}}</p>
                        <p><strong>Titolo originale:</strong> {{item.original_name}}</p>
                        <span><strong>Lingua:</strong> {{item.original_language}}</span>
                        <span><strong>Voto:</strong> {{item.vote_average}}</span>
                  </div>  
                  
                </div>
              </div>
              
          </div>
          
      </div>
  </main>
</template>

<script>

export default {
    // metto il nome del componente
    name: 'MainComp',

    // creo i data
    data(){
        return {

            // creo un dato che mi serve per caricare le immagini
            defaultImgUrl: 'https://image.tmdb.org/t/p/'
        }
    },

    props: {

        tvSeries: Array,

        films: Array
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

<style lang='scss' scoped>

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
                    // padding: 29px;
                    border: 1px solid darkgray;
                    border-radius: 5px;
                    margin-bottom: 20px;
                    margin-left: 2px;
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
                    }
                    
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
                    .series-description{
                        display: none;
                        flex-direction: column;
                        padding: 11px;
                        font-size: 12px;
                        row-gap: 6px;

                        p{
                            overflow-wrap: break-word;
                        }
                    }   strong{
                        color: gray;
                    }
                    
                }
            }
        }
    }


    // creo questa parte per gestire gli hover delle card
    .container{

        // hover dei FILM
        .movies-box{
            #movies-container{
                .movies-card:hover{
                    cursor: pointer;
                    img{
                        display: none;
                    }
                    .movie-description{
                        display: flex;
                        flex-direction: column;
                    }
                }
            }
        }

        // hover delle SERIE TV
        .tv-series-box{
            #tv-series-container{
                .series-card:hover{
                    cursor: pointer;
                    img{
                        display: none;
                    }
                    .series-description{
                        display: flex;
                        flex-direction: column;
                    }
                }
            }
        }
    }

    @media screen and (max-width: 850px) {
        .container{
            .movies-box{
                #movies-container{
                    .movies-card{
                        width: 31%;
                    }
                }
            }
             .tv-series-box{
                #tv-series-container{
                    .series-card{
                        width: 31%;
                    }
                }
            }
        }
        
        
    }

    @media screen and (max-width: 622px) {

        .container{
            .movies-box{
                #movies-container{
                    .movies-card{
                        width: 46%;
                    }
                }
            }
             .tv-series-box{
                #tv-series-container{
                    .series-card{
                        width: 46%;
                    }
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