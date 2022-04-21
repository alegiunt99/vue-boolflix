<template>
  <main>
      <div class="container">
          <div class="movies-box">
                <h1>MOVIES</h1>
                <div v-if="films.length > 0" id="movies-container">
                  <div class="movies-card" v-for="item in films" :key="item.id">
                    <h3>{{item.title}}</h3>
                    <p>{{item.original_title}}</p>
                    <span>{{item.original_language}}</span>
                    <span>{{item.vote_average}}</span>
                  </div>
                </div>
              
          </div>

          <div class="tv-series-box">
              <h1>TV SERIES</h1>
              <div v-if="tvSeries.length > 0" id="tv-series-container">
                <div class="series-card" v-for="item in tvSeries" :key="item.id">
                  <h3>{{item.name}}</h3>
                  <p>{{item.original_name}}</p>
                  <span>{{item.original_language}}</span>
                  <span>{{item.vote_average}}</span>
                </div>
              </div>
              
          </div>
          
      </div>
  </main>
</template>

<script>

export default {
    name: 'MainComp',

    props: {

        tvSeries: Array,

        films: Array
    },

    methods:{
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
                    text-align: center;
                    display: flex;
                    flex-direction: column;
                    row-gap: 2px;
                    justify-content: center;
                    padding: 29px;
                    border: 1px solid darkgray;
                    border-radius: 5px;
                    margin-bottom: 20px;
                    margin-left: 2px;
                    h3{
                        overflow-wrap: break-word;
                    }
                    p{
                        color: #959393;
                        overflow-wrap: break-word;
                    }
                    span{
                        font-size: 16px;
                        color: gray;
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
                    text-align: center;
                    display: flex;
                    flex-direction: column;
                    row-gap: 2px;
                    justify-content: center;
                    padding: 29px;
                    border: 1px solid darkgray;
                    border-radius: 5px;
                    margin-bottom: 20px;
                    margin-left: 2px;
                    h3{
                        overflow-wrap: break-word;
                    }
                    p{
                        color: #959393;
                        overflow-wrap: break-word;
                    }
                    span{
                        font-size: 16px;
                        color: gray;
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