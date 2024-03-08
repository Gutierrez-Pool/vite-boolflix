<script>
export default {
    name: 'AppCard',

    props: {
        item: Object,
    },

    methods: {
        // Immagini
        showImage(currentImage) {
            return `https://image.tmdb.org/t/p/w342${currentImage}`
        },

        // vote(currentVote) {
        //     return (currentVote / 2 )
        // },
        
        // voti
        voteStars(currentVote) {
            const fillStars = (currentVote / 2);

            const starArray = [];

            for (let i = 0; i < 5; i++) {
                let emptyStars =  'fas fa-star';

                if (i < fillStars) {
                    emptyStars += ' filled';
                }
                starArray.push(emptyStars);
            }
            return starArray;
        }
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
            <p><strong>Voto: </strong>
                <span v-for="emptyStars in voteStars(item.vote_average)" :key="emptyStars">
                   <i :class="emptyStars"></i>
                </span></p>
            <p><strong>Overview:</strong> {{ item.overview }}</p>
        </div>
    </li>


</template>

<style lang="scss">

.cards {
    display: flex;
    flex-flow: column;

    position: relative;
    
    width: calc(100% / 5 - 5px / 5 * 4);

    gap: .7em;


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
        opacity: 0;


        .fas.fa-star {
            color: rgba(255, 255, 255, 0.281);
        }

        .fas.fa-star.filled {
            color: gold;
        }
    }

    .card:hover {
        opacity: 0.85;    
    }

}

</style>