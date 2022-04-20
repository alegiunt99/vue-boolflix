<template>
  <header>
      <div id="logo-box">
          <img src="@/assets/netflix_logo.png" alt="logo">
      </div>
        
      <div id="search-box">
          <SearchBar @searchText="valoreRicerca"/>
      </div>
  </header>
</template>

<script>

import SearchBar from '@/components/SearchBar.vue'

export default {
    name: 'HeaderComp',

    data(){
        return {
            testoRicerca: '',
        }
        
    },

    components:{
        SearchBar
    },

    methods:{
        valoreRicerca(query){
            this.testoRicerca = query;

            console.log('Header riceve',this.testoRicerca)
        }
    }
}
</script>

<style lang='scss' scoped>

    header{
        display: flex;
        justify-content: space-between;
        background-color: #2a2a2a;
        #logo-box{
            width: 150px;
            img{
                width: 100%;
            }
        }
    }

</style>