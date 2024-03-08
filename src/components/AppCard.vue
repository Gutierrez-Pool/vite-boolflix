<script>
export default {
    name: 'AppCard',

    props: {
        item: Object,
    },

    methods: {
        showImage(currentImage) {
            return `https://image.tmdb.org/t/p/w342${currentImage}`
        },

    },

}
</script>

<template>

    <li class="cards">
    
        <img :src="showImage(item.poster_path)" :alt="item.title">
        
        <div class="card">
            <h3><strong>Titolo:</strong> {{ item.title ? item.title : item.name }}</h3>
            <h5><strong>Titolo originale:</strong> {{ item.original_title ? item.original_title : item.original_name }}</h5>
            <p>{{ item.original_language }}</p>
            <p><strong>Voto:</strong> {{ item.vote_average }}</p>
            <p><strong>Overview:</strong> {{ item.overview }}</p>
        </div>
    </li>


</template>

<style lang="scss">

.cards {
    display: flex;
    flex-flow: column;

    position: relative;

    gap: .7em;

    width: calc(100% / 5 - 5px / 5 * 4);

    // text-align: center;

    img {
        width: 100%;
        height: 336px;
    }

    .card {
        position: absolute;
        width: 100%;
        height: 336px;

        padding: 20px 13px;
        overflow-y: auto;
        background-color: black;
        // display: none;
        opacity: 0;
    }

    .card:hover {
        opacity: 0.85;    
    }
}

</style>