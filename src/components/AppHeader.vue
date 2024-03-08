<script>
import {store} from '../store'

export default {
    data() {
        return {
            store,
        }
    },
}

</script>

<template>

    
    <div class="container">

        <img src="https://fontmeme.com/permalink/240308/c889f5a620a7714ff1d7ba890a24079d.png" alt="netflix-font" border="0">

        <div id="search-bar">
            <input class="border" type="search" name="searchText" placeholder="Cerca" v-model="store.searchText">
            <button @click="$emit('search')" class="border">Cerca</button>
    
        </div>
    </div>
</template>

<style scoped>

.container {
    display: flex;
    justify-content: space-between;
    align-items: center;

    width: 100%;
    height: 120px;

    padding: 0 40px;
    background-color: #141414;

    #search-bar {
        display: flex;
        gap: 5px;

        .border{
            padding: 8px 12px;
            border-radius: 8px;
            border: 0px;
        }

        button {
            background-color: red;
        }
    }
}

</style>

