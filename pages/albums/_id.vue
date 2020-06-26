<template>
    <div class="container">
        <header>
            <nuxt-link to="/" class="button is-link is-light">Volver</nuxt-link>
            <h1 class="title">{{ album.title }}</h1>
        </header>
        <div class="columns is-multiline">
            <div 
                class="column is-one-quarter"
                v-for="photo in photos" 
                :key="photo.id">
                    
                    <img :src="photo.url" :alt="photo.title">
            </div>
        </div>
    </div>
</template>

<script>
import router from 'vue-router'
import axios from 'axios'
import config from '../../config/env'

export default {
    name: 'AlbumPage',
    data() {
        return {
            album: {},
            photos: []
        }
    },
    created: async function() {
        //console.log(this.$route)
        let albumId = this.$route.params.id;

        let resAlbum = await axios.get(`${config.urlBase}/albums/${albumId}`);
        this.album = resAlbum.data;

        let resPhotos = await axios.get(`${config.urlBase}/albums/${albumId}/photos`);
        this.photos = resPhotos.data;
    }

}
</script>

<style scoped>
    .container {
        text-align: center;
    }
</style>