<template>
  <header>
      <div id="logo-box">
          <img src="@/assets/netflix_logo.png" alt="logo">
      </div>
        
      <div id="search-box">
          <SearchBar />
      </div>
  </header>
</template>

<script>

import SearchBar from '@/components/SearchBar.vue'

export default {
    name: 'HeaderComp',

    components:{
        SearchBar
    },
}
</script>

<style lang='scss' scoped>

    header{
        display: flex;
        #logo-box{
            width: 150px;
            img{
                width: 100%;
            }
        }
    }

</style>