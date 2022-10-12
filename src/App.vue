<template>
<div class="app">
    <form @submit.prevent class="container">
        
        <div class="container_input">
            <input 
            class="input" 
            v-model.lazy="ip"
            placeholder="Напишите ip" 
            type="text">
        </div>
        <button class="btn" @click="findServer">Найти</button>
    </form>
    <ServerList :ip="ip"/>
       
</div>

</template>

<script>
import ServerList from "@/components/ServerList.vue";
export default{
    
    components: {
        ServerList
    },
    data() {
        return {
           ip: ''
        } 
    },
   
}
</script>

<style>
    *{
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }
    .app{
        padding: 20px;
    }
    .container{
        padding-left: 40%;
        display: inline-block;
    }
    .container_input{
        float: left;
    }
    .input{
        width: 100%;
        border: 1px solid teal;
        padding: 10px 15px;

    }
    .btn{
        border: 1px solid teal;
        padding: 10px 15px;
        background: none;
        color: teal;
    }
    

</style>