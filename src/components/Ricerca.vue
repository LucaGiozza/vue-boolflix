<template>
<form class="container">

    <div>
        <input class=" casella-ricerca" type="text" 
        placeholder="Ricerca film o Serie tv" v-model="inputText" >
    </div>
    <div>
        <button  type="submit" @click.prevent="$emit('search',inputText)"  >Search</button>
        <button  type="reset" >Reset</button>
    </div>


</form>
</template>

<script>
export default {
    name: 'Ricerca',
    data(){
        return{
            inputText: ''
        }
    }

}
</script>

<style lang="scss" scoped>
.container{
    display: flex;
    justify-content: flex-end;
    margin-right: 100px;
    .casella-ricerca{
        width:200px;
        height: 20px;
    }
    button{
        width:80px;
        height: 25px;
        margin-left:10px;
    }
}

</style>