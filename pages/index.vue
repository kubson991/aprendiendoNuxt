<template lang="html">
 
    <div class="container">
        <header><h1 class="title">Albums de la pagina</h1> </header>
        
        <div class="columns is-multiline">
            <album-card :album="album" v-for="album in albums" :key="album.id" /> 
        </div>
    </div>
        
</template>

<script>
import axios from 'axios'
import env from '../config/env'
import albumCard from '../components/albumCard.vue'
export default{
  components: { albumCard },
    name:'IndexPage',
    data(){
        return{
            albums:[]
        }
    },
    created(){
        axios.get(`${env.endpoint}/albums`).then(response=>this.albums=response.data) 
         
    }
}

</script>

<style scoped>

.title{
    text-align: center;
}

</style>