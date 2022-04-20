<template>
  <header>
      <div id="logo-box">
          <img src="@/assets/netflix_logo.png" alt="logo">
      </div>

      <div id="search-box">
          
      </div>
  </header>
</template>

<script>
export default {
    name: 'HeaderComp',
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