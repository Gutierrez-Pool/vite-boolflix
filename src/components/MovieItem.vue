<script>
export default {
    name: 'MovieItem',

    props: {
        movie: Object,
    },

}
</script>

<template>

    <li class="movie">
        <!-- <img :src="movie.poster_path" :alt="movie.title"> -->
        {{ movie.title }} <br>
        {{ movie.original_title }} <br>
        {{ movie.original_language }} <br>
        {{ movie.vote_average }}
        
    </li>


</template>

<style>

.movie {
    display: flex;
    flex-flow: column;
    gap: .7em;

    width: calc(100% / 4 - 20px / 4 * 3);

    text-align: center;
}

</style>