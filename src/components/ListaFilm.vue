<template>

   



<div>
   
    

    
        
         <h2 class="titolo"> Title: {{info.title || info.name}}</h2>
    <ul>
        <li> Oiginal title: {{info.original_title|| info.original_name}}</li>
         <li>{{info.original_language}}</li> 
         <div class="bandiere" v-if="flags.includes(info.original_language)">


             <img :src="require(`../assets/${info.original_language}.jpg`)" :alt="info.original_language"> 
             
         </div>
         <div class="flags" v-else>
             {{info.original_language}}

         </div>
         <li>
            
               {{info.poster_path}} 
        </li>

          
        <!-- <img src="https://www.countryflags.io/us/flat/64.png" >  -->
        <li> Vote: {{info.vote_average}}</li>
    </ul>
    <ul>
        
    </ul>

    
    

     

     <Animazione  /> 
     <!-- :details="film"  -->


</div>
  
</template>

<script>

 import Animazione from '@/components/Animazione.vue'

export default {
    name: 'ListaFilm',
    props: ['info'],
    components :{
         Animazione

    },
    data(){

        return{
            flags:["en", "it", "ja"],
             

        }
    },


        // methods: {
        //     // funzione per impostare un'immagine 
        //     getImages: function(element) {
        //         if(element.poster_path != null) {
        //             return 'https://image.tmdb.org/t/p/w600_' + element.poster_path;
        //         }

        //         return 'foto';
        //     },
        // }
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
.bandiere img{
    width:150px;
}
.flags{
    width:150px;
}

</style>