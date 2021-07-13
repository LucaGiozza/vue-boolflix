<template>
  <div>
    <img  class="fotografie" :src="details.poster" :alt="details.title">
    <h3 class="titolo">{{details.title}}</h3>
    <p class="autore">{{details.author}}</p>

  </div>
</template>

<script>
export default {
name: 'Animazione',
props:["details"]
}
</script>

<style lang="scss" scoped>

</style>