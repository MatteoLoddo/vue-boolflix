<template>
  <div id="app">
    <TheHeader @SearchText="onClickSearch"></TheHeader>
    <TheMain 
    :list-film-found="MoviesList"
    :currently-void="ThisVoid"></TheMain>
  </div>
</template>

<script>
import TheHeader from './components/TheHeader.vue'
import TheMain from './components/TheMain.vue'
import axios from "axios";

export default {

  name: 'App',
  components: {
    TheHeader, TheMain,
  },

  data() {
    return {
      UrlApiTMD:"https://api.themoviedb.org/3/search/movie/",
      MyApiKey:"b9719857ee7a2b1e4e77d019f7e50a4c",
      MoviesList:[],
      ThisVoid:false,
    }
  },
  methods: {
    onClickSearch(searchText) {
      this.MoviesList =[];
      axios.get (this.UrlApiTMD,{
        params:{
          api_key:this.MyApiKey,
          query:searchText,
          lang:"it-IT",

        }
      })
        .then((resp) => {
          console.log(resp);
          this.MoviesList.push(...resp.data.results)
          if(resp.data.results.length == 0){
            this.ThisVoid = true;
          }else{
            this.ThisVoid = false;
          }
        })
        .catch(()=>{
          alert('si e verificato un errore')
        })

    }

  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
