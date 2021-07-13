<template>
<div >
<p>{{info.title}}</p>
<p>{{info.original_title}}</p>
<p>{{info.original_language}}</p>
<p>{{info.vote_average}}</p>
     

    <Animazione :details="film" />

</div>
  
</template>

<script>
import axios from 'axios';
import Animazione from '@/components/Animazione.vue'

export default {
    name: 'ListaFilm',
    props: ['info'],
    components :{
        Animazione

    },
      data(){
        return{
            apiURL : 'https://api.themoviedb.org/3/search/movie?api_key=cabe8922195f2ff0cfd386b87a764c5b&query=luca',
            filmArray : '',
            semaforo: true
        }


    },
      created(){
        this.getFilm();

    },
    methods:{
        getFilm(){
            axios
            .get(this.apiURL)
            .then(risposta =>{
                
                this.filmArray = risposta.data.response;
                console.log(this.filmArray);
                this.semaforo = false;

            })
            .catch(error =>{
                console.log(error);
            })

        }
    }


}

</script>


<style lang="scss" scoped>

</style>