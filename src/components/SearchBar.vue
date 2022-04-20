<template>
  <div>
      <input v-model="query"  type="text" placeholder="cerca un film o serie tv">

      <button @click="$emit('searchText', query)">Cerca</button>
  </div>
</template>

<script>
export default {
    name: 'SearchBar',

    data(){
        return {
            query: ''
        }
    },

    /*computed:{
        showText(){

            if(this.query.length > 0){

                this.query = this.query.toLowerCase().trim();

                return this.$emit('textValue', this.query)
            }
            
            
        }
    }*/
}
</script>

<style lang='scss' scoped>

</style>