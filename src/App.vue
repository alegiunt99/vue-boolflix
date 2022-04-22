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

    // creo una funzione generale che collega il contenuto della searchbar con il main
    textValue(query){

      //mi accerto che non ci siano spazi
      let querys = query.trim();

      // collego il data del e il testo digitato nella searchbar
      this.searchedText = querys

      // successivamente 
      this.searchFilms(querys);

      this.searchTvSeries(querys);
      
    },

    // creo una funzione per ricevere i FILM con axios
    searchFilms(querys) {

      // creo i parametri indispensabili per la chiamata di axios
      let params = {
            query: querys,

            api_key: this.apiKey,
          
            language: 'it-IT',
          }

      // se il testo ricercato ha una lungezza maggiore di 0
      if(this.searchedText.length > 0){

          //faccio la chiamata axios per i film
          return axios.get(this.apiUrl + 'movie', { params }).then((risultato) => {
            
            console.log('films:', risultato.data.results)


            // ed equivalgo l'array dei film all'array del risultato 
            return this.films = risultato.data.results;

          })

      }
      
      return this.films = []
    },

    // creo una funzione per ricevere le SERIE TV con axios
    searchTvSeries(querys){

      // creo i parametri indispensabili per la chiamata di axios
      let params = {
            query: querys,

            api_key: this.apiKey,
          
            language: 'it-IT',
          }

      // se il testo ricercato ha una lungezza maggiore di 0
      if(this.searchedText.length > 0){

          //faccio la chiamata axios per le serie tv
          return axios.get(this.apiUrl + 'tv', { params }).then((risultato) => {
            
            
            console.log('serie tv: ',risultato.data.results)

            // ed equivalgo l'array delle serie tv all'array del risultato 
            return this.tvSeries = risultato.data.results;

          })

      }

      return this.tvSeries = []
    }

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
