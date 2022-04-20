<template>
  <main>
      <div class="container">
          <div class="movies-box">
              <h1>MOVIES</h1>
              <MovieCards />
          </div>

          <div class="tv-series-box">
              <h1>TV SERIES</h1>
              <TvSeriesCards/>
          </div>
          
      </div>
  </main>
</template>

<script>
import MovieCards from '@/components/MovieCard.vue'

import TvSeriesCards from '@/components/TvSeriesCard.vue'

export default {
    name: 'MainComp',

    components:{

        MovieCards,

        TvSeriesCards
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
</style>