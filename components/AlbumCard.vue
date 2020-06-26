<template>
    <div class="column is-one-quarter">
        <div class="box">
            <h3>{{ album.title }}</h3>
            <nuxt-link :to="`/albums/${album.id}`" class="button is-primary">Ver más</nuxt-link>
        </div>
    </div>
</template>

<script>
export default {
    name: 'AlbumCard',
    props: {
        album: Object
    }
}
</script>

<style>
    .box {
        padding: 0.5rem;
    }

    h3 {
        min-height: 5em;
    }
</style>