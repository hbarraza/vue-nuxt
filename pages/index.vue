<template>
    <div class="container">
        <header>
            <h1 class="title">Álbums de la página</h1>
        </header>
        <div class="columns is-multiline">
            <AlbumCard 
                :album="album" 
                v-for="album in albums" 
                :key="album.id"/>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
import config from '../config/env'
import AlbumCard from '../components/AlbumCard'

export default {
    name: 'initPage',
    data(){
        return {
            albums: []
        }
    },
    created: async function() {
        let resData = await axios.get(`${config.urlBase}/albums`);
        this.albums = resData.data;
    },
    components: {
        AlbumCard
    }
}
</script>

<style scoped>

</style>