<template>
  <header>
      <!-- Logo di netflix -->
      <div id="logo-box">
          <img src="@/assets/netflix_logo.png" alt="logo">
      </div>

        <!-- input text per cercare film e serie -->
      <div id="search-box">

            <input v-model="query"  type="text" placeholder="cerca un film o serie tv" @keyup.enter="$emit('searchText', query)">

            <button @click="$emit('searchText', query)">Cerca</button>

      </div>
  </header>
</template>

<script>

export default {
    name: 'HeaderComp',

    data(){
        return {
            query: '',
        }
        
    },
}
</script>

<style lang='scss' scoped>

    header{
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: #2a2a2a;
        #logo-box{
            width: 150px;
            img{
                width: 100%;
            }
        }
        #search-box{
            padding-right: 10px;
            display: flex;
            column-gap: 7px;
            input{
                font-size: 12px;
                padding: 6px;
                background-color: #383838;
                color: rgb(189, 189, 189);
                border: none;
                border-radius: 7px;
                &:focus-visible{
                    outline: none;
                }
            }
            button{
                font-size: 13px;
                padding: 5px;
                color: rgb(189, 189, 189);
                border-radius: 5px;
                background-color: #444444;
            }
        }
    }

    @media screen and (max-width: 370px) {

        header{
            #logo-box{
                img{
                    width: 49%;
                }
            }

            #search-box{
                width: 43%;
                input{
                    width: 100%;
                }
                button{
                    display: none;
                }
            }
        }
        
    }

</style>