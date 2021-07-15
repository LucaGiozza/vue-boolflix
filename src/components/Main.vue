<template>
<div class="main">
    
    <Ricerca @search="ricercaFilm" />

    <div>
        <h2>Film in lista :</h2>
        <ListaFilm v-for="film in filmsArray" :key="film.id" :info="film"/>
    </div>
    <div>
        <h2>Serie tv in lista:</h2>
        <ListaFilm v-for="serieTv in tvArray" :key="serieTv.id" :info="serieTv"/>
        

    </div>
    <!-- <div>
        
        <ListaFilm v-for="serieTv in tvArray" :key="serieTv.id" :info="serieTv"/>
        

    </div> -->
   
   

    
    
    

</div>
  
</template>


<script>
import axios from 'axios';

import Ricerca from '@/components/Ricerca.vue';
import ListaFilm from '@/components/ListaFilm.vue';

export default {
    name: 'Main',
  
   
    components: {
       Ricerca,
       ListaFilm
      
  },
 
  data(){
      return {
          apiUrl:'https://api.themoviedb.org/3/search/movie',
          apiTvUrl:'https://api.themoviedb.org/3/search/tv',
           copertinaApiUrl:'https://image.tmdb.org/t/p/w342/dOsASSkNxUjtEp47eSDNazDPDPa.jpg',
          

          apiKey: 'cabe8922195f2ff0cfd386b87a764c5b',
          language:'it-IT',
        //    listaFilms : '',
        //    listaSeries:'',
          
           searchText :'',
        //    searchTextTv: '',
           filmsArray: '',
           tvArray: '',
           copertinaArray : ''
         
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
               axios.get(this. apiTvUrl, request),
               axios.get(this.copertinaApiUrl, request)
           ])

           .then(axios.spread((responseFilm, responseTv, responseCopertina) => {
               this.filmsArray= responseFilm.data.results;
               this.tvArray= responseTv.data.results;
               this.copertinaArray = responseCopertina.data.results;
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
h2{
    color:red;
}

</style>