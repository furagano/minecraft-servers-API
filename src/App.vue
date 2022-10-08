<template>
<div class="app">
    <form @submit.prevent class="container">
        
        <div class="container_input">
            <input 
            class="input" 
            @input="ip = $event.target.value"
            placeholder="Напишите ip" 
            :value="ip" 
            type="text">
        </div>
        <button class="btn" @click="findServer">Найти</button>
    </form>
    <ServerList :servers="servers"/>
       
</div>

</template>

<script>
import ServerList from "@/components/ServerList.vue";
export default{
    
    components: {
        ServerList
    },
    data() {
        ip: ' '
    },
    methods: {
        findServer(){
            const newServer = {
                id: Date.now(),
                ip: this.ip
            }
            this.ServerList.servers.push(newServer);
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