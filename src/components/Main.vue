<template>
<div class="main">
    <Ricerca @search="ricercaFilm"/>

</div>
  
</template>


<script>
import Ricerca from '@/components/Ricerca.vue'
export default {
    name: 'main',
    components: {
       Ricerca
  },
  methods :{

      ricercaFilm(trovaFilm){
        console.log('ciao', trovaFilm);
      }
  }

}
</script>

<style lang="scss" scoped>

</style>