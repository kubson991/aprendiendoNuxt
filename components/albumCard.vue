<template>
    <div class=" column is-one-quarter is-three-quarters-mobile">
        <div class="box">
        <h3>{{album.title}}</h3>
        <nuxt-link :to="`/albums/${album.id}`" class="button is-primary">ver album</nuxt-link>
        </div>

    </div>   
</template>

<script>
export default {
    name:'albumCard',
    props:{
        album:Object,
    }
}
</script>

<style scoped>
    h3{
        min-height: 4.5em;
    }
</style>