<template>
   
        <div class="app"> 
            <form @submit.prevent class="container">
                
                <div class="container_input">
                    <input 
                    class="input" 
                    v-model.lazy="ip"
                    placeholder="Напишите ip" 
                    type="text">
                    <button class="btn" @click="findServer">Найти</button>
                </div>
                
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
        margin-top: 20px;
        
    }
   
    .container{
        margin-left: 40%;
    }
    .input{
        width: 25%;
        border: 1px solid rgb(255, 255, 255);
        padding: 10px 15px;
        background:rgba(0, 0, 0, 0.8);
        color: white;
    }
    .input::placeholder{color: white;}
    .btn{
        border: 1px solid rgb(255, 255, 255);
        padding: 10px 15px;
        background:rgba(0, 0, 0, 0.8);
        color: rgb(255, 255, 255);
    }
    

</style>