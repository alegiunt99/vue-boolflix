<template>
  <main>
      <div class="container">
          <div class="movies-box">
                <h1>MOVIES</h1>
                <div v-if="films.length > 0" id="movies-container">
                  <div class="movies-card" v-for="item in films" :key="item.id">
                    <img :src="createImagePath('/w342', item.backdrop_path)" alt="">
                    <div class="movie-description">
                        <p>Titolo: {{item.title}}</p>
                        <p>Titolo originale: {{item.original_title}}</p>
                        <span>Lingua: {{item.original_language}}</span>
                        <span>Voto: {{item.vote_average}}</span>
                    </div>              
                  </div>
                </div>
              
          </div>

          <div class="tv-series-box">
              <h1>TV SERIES</h1>
              <div v-if="tvSeries.length > 0" id="tv-series-container">
                <div class="series-card" v-for="item in tvSeries" :key="item.id">
                  <img :src="createImagePath('/w342', item.backdrop_path)" alt=""> 
                  <div class="series-description">
                        <p><strong>Titolo</strong>: {{item.name}}</p>
                        <p><strong>Titolo originale</strong>: {{item.original_name}}</p>
                        <span> <strong>Lingua</strong>: {{item.original_language}}</span>
                        <span><strong>Voto</strong>: {{item.vote_average}}</span>
                  </div>  
                  
                </div>
              </div>
              
          </div>
          
      </div>
  </main>
</template>

<script>
//import axios from 'axios'

export default {
    name: 'MainComp',

    data(){
        return {

            defaultImgUrl: 'https://image.tmdb.org/t/p/'
        }
    },

    props: {

        tvSeries: Array,

        films: Array
    },

    methods:{

        createImagePath(height, imgName){
            const totalPath = this.defaultImgUrl + height + imgName

            return totalPath
        }
    }
}
</script>

<style lang='scss' scoped>
    .container{
        max-width: 90%;
        margin: 50px auto;
        display: flex;
        flex-direction: column;
        color: white;
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
                    }
                    
                }
            }
        }
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
                    }
                    
                }
            }
        }
    }

    .container{
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