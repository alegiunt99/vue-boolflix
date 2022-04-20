<template>
  <div id="app">
    <!-- Header con logo e searchbar -->
    <HeaderComp />

    <!-- contenitore delle card di film e serie ricercati -->
    <MainComp/>
  </div>
</template>

<script>

import HeaderComp from '@/components/HeaderCom.vue';

import MainComp from '@/components/MainComp.vue';

export default {
  name: 'App',
  components: {

    HeaderComp,

    MainComp
  }
}
</script>

<style lang="scss">

</style>
