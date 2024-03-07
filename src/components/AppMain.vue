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

        <div class="movies">
            <h2>Movies</h2>
            <ul>
                <AppCard
                    v-for="currentMovie in store.movies"
                    :item="currentMovie"
                >
                </AppCard>
            </ul>
        </div>

        <div class="series">
            <h2>Series TV</h2>
            <ul>
                <AppCard
                    v-for="currentSerie in store.series"
                    :item="currentSerie"
                >
                </AppCard>
            </ul>
        </div>


    </div>

</template>

<style>

ul {
    list-style-type: none;

    display: flex;
    flex-flow: row wrap;

    margin: 50px 0px;
    gap: 5px;
}

</style>./AppCard.vue/index.js