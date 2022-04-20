<template>
  <div id="app">
    <!-- Header con logo e searchbar -->
    <HeaderComp @searchText="textValue"/>

    <!-- contenitore delle card di film e serie ricercati -->
    <MainComp/>
  </div>
</template>

<script>

// import axios from 'axios'; 

import HeaderComp from '@/components/HeaderCom.vue';

import MainComp from '@/components/MainComp.vue';

export default {
  name: 'App',

  data(){
    return {
      searchedText: '',
    }
  },

  components: {

    HeaderComp,

    MainComp
  },

  methods: {
    textValue(query){
      this.searchedText = query;

      console.log('App Vue riceve', this.searchedText);
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
