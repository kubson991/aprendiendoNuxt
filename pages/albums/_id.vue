<template>
    <div class="container">
        <header>
            <h1 class="title">{{album.title}}</h1>
            <nuxt-link to="/" class="back">regresar</nuxt-link>
        </header>

        <div class="columns is-multiline">
            <div class="column is-one-quarter" v-for="photo in photos" :key="photo.id">
                <img :src="photo.url" alt="photo.title">
            </div>
        </div>
    </div>
</template>
<script>
import router from 'vue-router'
import env from '../../config/env'
export default {
    name:'AlbumIndividualPage',
    data(){
        return{
            album:{},
            photos:[]
        }
    },
    async created(){
        let data=await (await fetch(`${env.endpoint}/albums/${this.$route.params.id}`)).json()   
        let dataPhotos=await (await fetch(`${env.endpoint}/albums/${this.$route.params.id}/photos`)).json()      
        this.photos=dataPhotos
        this.album=data
    }
}
</script>\

<style scoped>

    header{
        margin-bottom:20px ;
    }
    .back{
        padding: 5px;
 
    }
    .container{
        text-align: center;
    }
</style>