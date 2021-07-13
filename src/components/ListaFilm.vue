<template>

   



<div>
   
    

    
        
         <h2 class="titolo">{{info.title}}</h2>
    <ul>
        <li>{{info.original_title}}</li>
        <!-- <li>{{info.original_language}}</li> -->
       <img src="https://www.countryflags.io/us/flat/64.png" >
        <li>{{info.vote_average}}</li>
    </ul>

    
    

     

    <Animazione :details="film"  />


</div>
  
</template>

<script>
// import axios from 'axios';
import Animazione from '@/components/Animazione.vue'

export default {
    name: 'ListaFilm',
    props: ['info',],
    components :{
        Animazione

    }
}
//       data(){
//         return{
//             apiURL : 'https://api.themoviedb.org/3/search/movie?api_key=cabe8922195f2ff0cfd386b87a764c5b&query=luca',
//             filmArray : '',
//             semaforo: true,
             
//         }
       


//     },
//       created(){
//         this.getFilm();

//     },
//     methods:{
//         getFilm(){
//             axios
//             .get(this.apiURL)
//             .then(risposta =>{
                
//                 this.filmArray = risposta.data.response;
//                 console.log(this.filmArray);
//                 this.semaforo = false;

//             })
//             .catch(error =>{
//                 console.log(error);
//             })

//         },

       
//     }


// }

</script>


<style lang="scss" scoped>
.titolo{
    margin-top:90px;
}

</style>