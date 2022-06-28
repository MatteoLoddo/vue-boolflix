<template>
  <div>
    <div >
      <h2 v-if="(CurrentlyVoid)">Nessun Risultato Trovato</h2>
    <h2  v-else-if="(ListFilmFound.length == 0)">Cerca un film</h2>
    
    </div>
    <ul>
      <li v-for="(films, i) in ListFilmFound" :key="i" class="p-3">
        <span>{{films.title}}</span><br>
        <span>{{films.original_title}}</span><br>
        <span >{{films.original_language}}</span><br>
        <span>{{films.vote_average}}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "TheMain",
  props: {
    CurrentlyVoid:Boolean,
    ListFilmFound:Array,

  },

  data() {
    return {
    }
  },


  methods: {
    movieSearch() {
      

    },

  },

    mounted() {
      
    },
}
</script>

<style>
</style>
