<template>
<div class="main">
    <p>{{campoRicerca}}</p>
    <Ricerca @search="ricercaFilm"/>

    <ListaFilm v-for="film in filmsArray" :key="film.id" :info="film"/>

</div>
  
</template>


<script>
import axios from 'axios';

import Ricerca from '@/components/Ricerca.vue';
import ListaFilm from '@/components/ListaFilm.vue';
export default {
    name: 'main',
  
   
    components: {
       Ricerca,
       ListaFilm
  },
 
  data(){
      return {
          apiUrl:'https://api.themoviedb.org/3/search/movie',
          apiKey: 'cabe8922195f2ff0cfd386b87a764c5b',
          listaFilm : '',
         searchText :'',
         filmsArray: []
      }
      
  },
  computed:{
      filtroFilm(){
          return this.listaFilm.filter(element => {
             return element.name.includes(this.searchText.toLowerCase())
          });

          
      }



  },
  methods :{

      ricercaFilm(trovaFilm){
          this.searchText= trovaFilm
          axios
              .get(this.apiUrl,{
                  params:{
                      api_key: this.apiKey,
                      query: trovaFilm
                  }
              })
              .then(response => {
                  console.log(response.data.results);
                  this.filmsArray= response.data.results;
              });
          
          console.log( this.searchText);
      }
  }

}
</script>

<style lang="scss" scoped>

</style>