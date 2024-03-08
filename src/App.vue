<script>
import axios from 'axios';
import { faFontAwesome } from '@fortawesome/free-solid-svg-icons';
import {store} from './store.js';

import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';

export default {
  data() {
    return {
      movies: [],
      series: [],

      store,
    }
  },

  components: {
    AppHeader,
    AppMain,
  },

  methods: {
    searchMovies() {
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=e9b9b757bb90674f79be808842a884de&language=it_IT&query=' + this.store.searchText).then(res => {
        console.log(res.data.results)
        this.store.movies = res.data.results;
      })
    },

    searchSeries() {
      axios.get('https://api.themoviedb.org/3/search/tv?api_key=e9b9b757bb90674f79be808842a884de&language=it_IT&query=' + this.store.searchText).then(res => {
        console.log(res.data.results)
        this.store.series = res.data.results;
      })
    },

  }
}

</script>

<template>
  
  <AppHeader @search="searchMovies(), searchSeries()"></AppHeader>

  <AppMain></AppMain>

</template>

<style>

</style>
