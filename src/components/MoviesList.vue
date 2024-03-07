<script>
import MovieItem from "./MovieItem.vue";

import {store} from '../store.js';

export default {
    name: 'MoviesList',

    components: {
        MovieItem,
    },

     data() {
        return {
            store,
        }
     },

     
    }
</script>

<template>

    <div class="container">

        <ul>

            <MovieItem
                v-for="currentMovie in store.movies"
                :movie="currentMovie"
            >
            </MovieItem>

        </ul>

    </div>

</template>

<style>

ul {
    list-style-type: none;

    display: flex;
    flex-flow: row wrap;

    margin: 50px 0px;
    gap: 20px;
}

</style>