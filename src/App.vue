<script>

import axios from 'axios';
import {store} from './store.js';

import Search from './components/Search.vue';
import MoviesList from './components/MoviesList.vue';

export default {
  data() {
    return {
      movies: [],

      store,
    }
  },

  // created() {
  //   axios.get('https://api.themoviedb.org/3/search/movie/top_rated?api_key=e9b9b757bb90674f79be808842a884de').then(res => {
  //     console.log('movies', res.data.results)
  //   })
  // },

  components: {
    Search,
    MoviesList,
  },

  methods: {
    searchMovies() {
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=e9b9b757bb90674f79be808842a884de&query=' + this.store.searchText).then(res => {
        console.log(res.data.results)
        this.store.movies = res.data.results;
      })
    }
  }
}

</script>

<template>
  
  <Search @search="searchMovies()"></Search>

  <MoviesList></MoviesList>


</template>

<style>

</style>
