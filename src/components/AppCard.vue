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
        },

        // bandiere
        changeFlags (currentLanguage) {

            if (currentLanguage === 'en') {
                currentLanguage = 'us'
            } 
            else if (currentLanguage === 'ja') {
                currentLanguage = 'jp'
            }
            else if (currentLanguage === 'ko') {
                currentLanguage = 'kr'
            }
            // per aggiungere altre bandiere
            // else if (currentLanguage === '') {
            //     currentLanguage = ''
            // }

            return `https://flagcdn.com/w40/${currentLanguage}.jpg`
        },

    },

}


</script>

<template>

    <li class="cards">
    
        <img v-if="item.poster_path" :src="showImage(item.poster_path)" :alt="item.title">
        <img v-else src="https://www.altavod.com/assets/images/poster-placeholder.png" alt="">
        
        <div class="card">
            <h3><strong>Titolo:</strong> {{ item.title ? item.title : item.name }}</h3>

            <h5><strong>Titolo originale:</strong> {{ item.original_title ? item.original_title : item.original_name }}</h5>

            <img :src="changeFlags(item.original_language)" alt="">

            <p><strong>Voto: </strong>
                <span v-for="emptyStars in voteStars(item.vote_average)">
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

        display: flex;
        flex-flow: column;

        width: 100%;
        height: 336px;

        gap: 10px;
        padding: 20px 13px;
        overflow-y: auto;

        background-color: black;
        opacity: 0;

        img {
            width: 30px;
            height: auto;
        }

        .fas.fa-star {
            color: rgba(255, 255, 255, 0.281);
        }

        .fas.fa-star.filled {
            color: rgb(226, 241, 7);
        }
    }

    .card:hover {
        opacity: 0.85;    
    }

}

</style>