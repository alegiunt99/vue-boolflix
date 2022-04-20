<template>
  <main>
      <div class="container">
          <div class="movies-box">
              <h1>MOVIES</h1>
              <div v-for="item in films" :key="item.id">
                  <p>{{item.title}}</p>
              </div>
          </div>

          <div class="tv-series-box">
              <h1>TV SERIES</h1>
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
        cov(){
            console.log(this.films)
        }
    }
}
</script>

<style lang='scss' scoped>
    .container{
        max-width: 80%;
        margin: 50px auto;
        display: flex;
        flex-direction: column;
        .movies-box{
            display: flex;
            flex-direction: column;
        }
        .tv-series-box{
            display: flex;
            flex-direction: column;
        }
    }

    h1{
        color:white;
    }
    
</style>