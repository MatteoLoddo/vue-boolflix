<template>
  <div>
    <div >
      <h2 v-if="(CurrentlyVoid)">Nessun Risultato Trovato</h2>
    <h2  v-else-if="(ListFilmTvFound.length == 0)">Cerca un film</h2>
    
    </div>
    <ul class="list-unstyled">
      <li v-for="(films, i) in ListFilmTvFound" :key="i" class="p-3">
        <strong class="text-danger" v-if="(films.name)">SERIE TV</strong>
        <strong class="text-primary" v-else>FILM</strong><br>
        <span> <strong >TITLE: </strong>{{films.title||films.name}}</span><br>
        
        <div v-if="(films.original_title != films.title)"> <strong>Original TITLE: </strong>{{films.original_title}}</div>
        <span> <strong>LANG: </strong>{{films.original_language}}</span><br>
        <span> <strong>VOTE: </strong>{{parseInt(parseFloat(films.vote_average))}}/10</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "TheMain",
  props: {
    CurrentlyVoid:Boolean,
    ListFilmTvFound:Array,

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
