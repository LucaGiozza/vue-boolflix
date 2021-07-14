<template>
<div class="main">
    <!-- <p>{{campoRicerca}}</p> -->
    <Ricerca @search="ricercaFilm" />

    <div>
        <h2>Film in lista :</h2>
        <ListaFilm v-for="film in filmsArray" :key="film.id" :info="film"/>
    </div>
    <div>
        <h4>Serie tv in lista:</h4>
        <ListaFilm v-for="serieTv in tvArray" :key="serieTv.id" :info="serieTv"/>

    </div>

    
    
    <ListaSerie />

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
          language:'it-IT',
           listaFilms : '',
           listaSeries:'',
          
           searchText :'',
           searchTextTv: '',
           filmsArray: '',
           TvArray: ''
         
      }
      
  },
  computed:{
      filtroFilm(){
          return this.listaFilm.filter(element => {
             return element.name.includes(this.searchText.toLowerCase())
          });

          
      },

     



  },

  methods :{

      ricercaFilm(trovaFilm){
          this.searchText= trovaFilm;
          const request = {
               params:{
                      api_key: this.apiKey,
                      language: this.language,
                      query: trovaFilm,
                      
                   }

          };
          // chiamata con metodo all

          axios
           .all([
               axios.get(this.apiUrl, request),
               axios.get(this. apiTvUrl, request)
           ])

           .then(axios.spread((responseFilm, responseTv) => {
               this.filmsArray= responseFilm.data.results;
               this.tvArray= responseTv.data.results;
            //    console.log(this.tvArray)


           }));

        //   prima chiamata
        //   axios
        //       .get(this.apiUrl,{
        //           params:{
        //               api_key: this.apiKey,
        //               query: trovaFilm,
                      
        //           }
        //       })
        //       .then(response => {
        //           console.log(response.data.results);
        //           this.filmsArray= response.data.results;
        //       });

        

        



            
          
          
      },

   
      
  }

}
</script>

<style lang="scss" scoped>

</style>