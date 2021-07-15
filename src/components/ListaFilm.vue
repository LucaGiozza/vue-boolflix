<template>

   



<div class="container-lista">
   
    
 <div class="copertina">
     <div class="sparisci" >
        <img class="foto-film"  v-if="info.poster_path != null" :src="`https://image.tmdb.org/t/p/w342/${info.poster_path}`" alt=""> 
             <div  v-else>
        <img class="netflix" src="@/assets/net.png" alt="">

   </div>
   
     
  

     </div>
   
  
      <div class="descrizione">
             <h2 class="titolo">  {{info.title || info.name}}</h2>
    <ul>
        <li class="original-title"> Oiginal title: {{info.original_title|| info.original_name}}</li>
        <li> vote:  {{info.vote_average}}</li>
         
         <div class="bandiere" v-if="flags.includes(info.original_language)">


             <img :src="require(`../assets/${info.original_language}.jpg`)" :alt="info.original_language"> 
             
         </div>
         <div class="flags" v-else>
             {{info.original_language}}

         </div>
         
        
    </ul>

    </div>

</div>
 
        
    
    

    
    

     

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
.copertina{
    position:relative;
    height:280px;
    
    .foto-film{
        height:300px;
        width: 80%;
        height:90%;
    }
    
}

.netflix{
    height: 300px;
     width:200px;
}

.container-lista{
    height:500px;
  text-align: center;
   
    width:calc(100% / 6 );
    
    float:left;
      
   
    .descrizione{
        position: absolute;
        top:2%;
        color:red;
       
      
        
    }
    
}
.titolo{
    width:70%;
    font-size:18px;
    margin:10px 0;
    margin-left: 20px;
    margin:auto;
    
    
   
}
.original-title{
    width:50%;
    font-size:12px;
    margin:10px 0;
    
}
.bandiere img{
    width:80px;
    margin-top:20px ;
    
}
.flags{
    width:150px;
}
ul li{
    
}
.copertina :hover{
      img{
    //  display:none;
    position:absolute;

     left:-9999px;
 

}




}
  
 



</style>