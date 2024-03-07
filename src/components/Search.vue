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

        <div id="search-bar">

            <input type="search" name="searchText" placeholder="Cerca" v-model="store.searchText">
            <button @click="$emit('search')" class="btn">Vai</button>
    
        </div>
    </div>
</template>

