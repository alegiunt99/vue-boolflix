<template>
  <div id="app">
    <!-- Header con logo e searchbar -->
    <HeaderComp @searchText="textValue"/>

    <!-- contenitore delle card di film e serie ricercati -->
    <MainComp :films="films" :tvSeries="tvSeries"/>
  </div>
</template>

<script>

  import axios from 'axios'; 

  import HeaderComp from '@/components/HeaderCom.vue';

  import MainComp from '@/components/MainComp.vue';

  export default {
  name: 'App',

  data(){
    return {
      apiUrl: 'https://api.themoviedb.org/3/search/',

      apiKey: '22b16fc2d767c4897f8b30b2f64c072c',

      searchedText: '',

      searching: false,

      films: [],

      tvSeries: [],

    }
  },

  components: {

    HeaderComp,

    MainComp
  },


  methods: {

    textValue(query){

      const querys = query.trim();

      if(querys.length > 0){
        this.searchedText = querys

        console.log(this.searchedText)
      }

      this.searchDs(querys)

      
    },

    searchDs(ccs) {


      let params = {
            query: ccs,

            api_key: this.apiKey,
          
            language: 'it-IT',
          }


      if(this.searchedText.length > 0){

          return axios.get(this.apiUrl + 'movie', { params }).then((risultato) => {
            
            console.log(risultato.data.results)
            return this.films = risultato.data.results;

          })

        
      }
      
    },

  }

}
</script>

<style lang="scss">
  *{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    
  }

  body{
    background-color: #383838;
  }
</style>
