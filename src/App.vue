<template>
  <div id="app">
    <header>
      <Header/>

    </header>

    <main>

      <Main />
      <!-- :films="filmsArray"  -->

    </main>
    
  </div>
</template>

<script>


import Header from './components/Header.vue'
import Main from './components/Main.vue'
export default {
  name: 'App',
  components: {
    Header,
    Main
  }
}
</script>

<style lang="scss">
html{
  background-color: black;;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  margin:0;
  padding:0;
  background-color: black;
  width:100%;
  
 
 
}
 
</style>
