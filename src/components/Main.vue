<template>
<div class="main">
    <!-- <p>{{campoRicerca}}</p> -->
    <Ricerca @search="ricercaFilm" />

    <ListaFilm v-for="film in filmsArray" :key="film.id" :info="film"/>
    <ListaSerie v-for="serie in serieTvArray" :key="serie.id" :info="serie"/>

</div>
  
</template>


<script>
import axios from 'axios';

import Ricerca from '@/components/Ricerca.vue';
import ListaFilm from '@/components/ListaFilm.vue';
import ListaSerie from '@/components/ListaSerie.vue';
export default {
    name: 'main',
  
   
    components: {
       Ricerca,
       ListaFilm,
       ListaSerie
  },
 
  data(){
      return {
          apiUrl:'https://api.themoviedb.org/3/search/movie',
          apiTvUrl:'https://api.themoviedb.org/3/search/tv',
          apiKey: 'cabe8922195f2ff0cfd386b87a764c5b',
           listaFilms : '',
           listaSeries:'',
          
           searchText :'',
           searchTextTv: '',
         filmsArray: [],
         serieTvArray: []
         
      }
      
  },
  computed:{
      filtroFilm(){
          return this.listaFilm.filter(element => {
             return element.name.includes(this.searchText.toLowerCase())
          });

          
      },

      filtroSerie(){
          return this.listaSeries.filter(element=> {
               return element.name.includes(this.searchTextTv.toLowerCase())

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
                      query: trovaFilm,
                      
                  }
              })
              .then(response => {
                  console.log(response.data.results);
                  this.filmsArray= response.data.results;
              });
          
          console.log( this.searchText);
      },

      ricercaSerie(trovaSerie){
          this.searchSeries = trovaSerie

          axios
              .get(this.apiTvUrl,{
                  params:{
                      api_key : this.apiKey,
                      query : trovaSerie
                  }

              })
              .then(response =>{
                  console.log(response.data.results);
                  this.serieTvArray = response.data.results;

              });


      }
      
  }

}
</script>

<style lang="scss" scoped>

</style>