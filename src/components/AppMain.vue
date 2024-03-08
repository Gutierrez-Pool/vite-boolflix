<script>
import AppCard from "./AppCard.vue";

import {store} from '../store.js';

export default {
    name: 'AppMain',

    components: {
        AppCard,
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

        <div class="movies" v-if="store.movies.length">
            <h1>Movies</h1>
            <ul>
                <AppCard
                    v-for="currentMovie in store.movies"
                    :item="currentMovie"
                >
                </AppCard>
            </ul>
        </div>

        <div class="series" v-if="store.movies.length">
            <h1>Series TV</h1>
            <ul>
                <AppCard
                    v-for="currentSerie in store.series"
                    :item="currentSerie"
                >
                </AppCard>
            </ul>
        </div>

        <h1 v-if="!store.searchText"><i>Cerca qualcosa...</i></h1>
    </div>

</template>

<style>

h1 {
    padding-top: 35px;
}

ul {
    list-style-type: none;

    display: flex;
    flex-flow: row wrap;

    margin: 20px 0px;
    gap: 5px;
}

</style>