<script>
export default {
    name: 'AppCard',

    props: {
        // movie: Object,
        // serie: Object,
        item: Object,
    },

    methods: {
        showImage(currentImage) {
            return `https://image.tmdb.org/t/p/w342${currentImage}`
        }
    },

}
</script>

<template>

    <li class="cards">
        <div>
            <img :src="showImage(item.poster_path)" :alt="item.title">
        </div>

        <div class="card">
            <h3>
                {{ item.title ? item.title : item.name }}
            </h3>
            <h5>
                {{ item.original_title ? item.original_title : item.original_name }}
            </h5>
            {{ item.original_language }} <br>
            {{ item.vote_average }}
        </div>
    </li>


</template>

<style lang="scss">

.cards {
    display: flex;
    flex-flow: column;
    gap: .7em;

    width: calc(100% / 5 - 5px / 5 * 4);

    text-align: center;

    img {
        width: 100%;
        height: 336px;
    }

    // .card {
    //     display: flex;
    // }

    // .card:hover {
    //     display: none;
    // }
}

</style>