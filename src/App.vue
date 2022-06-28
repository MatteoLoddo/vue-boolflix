<template>
  <div id="app">
    <TheHeader @SearchText="onClickSearch"></TheHeader>
    <TheMain 
    :list-film-tv-found="MoviesList"
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
      SearchMovie:"movie/",
      SearchTv:"tv/",
      UrlApiTMD:"https://api.themoviedb.org/3/search/",
      MyApiKey:"b9719857ee7a2b1e4e77d019f7e50a4c",
      MoviesList:[],
      ThisVoid:false,
    }
  },
  methods: {
    callToApi(searchText, type){

      axios.get (this.UrlApiTMD + type,{
        params:{
          api_key:this.MyApiKey,
          query:searchText,
          lang:"it-IT",

        }
      })
        .then((resp) => {
          console.log(resp);
          this.MoviesList.push(...resp.data.results)
          if(this.MoviesList.length == 0){
            this.ThisVoid = true;
          }else if(this.MoviesList.length > 0){
            this.ThisVoid = false;
          }
        })

        .catch(()=>{
          alert('si e verificato un errore: Impossibile lasciare l area di ricerca vuota')
        })

    },
    onClickSearch(searchText,) {
      this.MoviesList=[],
      this.ThisVoid = false,
      this.callToApi(searchText,this.SearchMovie )
      this.callToApi(searchText,this.SearchTv )
      

    },

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
