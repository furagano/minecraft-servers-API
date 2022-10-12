<template>
    <div class="server" v-for="server in servers" :key="server.favicon_base64">
        <template v-if="server.error">
            <div>not found 404</div>
        </template>
        <template v-else>
            <div class="server_image"><img :src="server.favicon" alt="Картинка"></div>
            <div><strong>Онлайн:</strong> {{server.online}} </div>
            <div><strong>Игроков:</strong> {{server.players.online}} из {{server.players.max}} </div>
            <div><strong>Версия:</strong> {{server.version.name}} </div>    
        </template>
    </div>
</template>
<script>
export default {
    props:{
        ip:{
            type: String,
            required: false,
            default: ''
        }
    },
    data(){
        return {
            servers: []
        }
    },
    
    methods(){
        
    },
    watch:{
        ip:{
            async handler(value){    
                const server = (await this.axios.get('https://eu.mc-api.net/v3/server/ping/' + value)).data;
                this.servers.push(server);
            },
            immediate: true
        }
    }
    
}
</script>
<style scoped>
    .server{
        margin-inline: 10%;
        margin-top: 20px;
        background-color: rgba(0, 0, 0, 0.8);
        padding: 30px;
        border: 3px solid rgb(255, 255, 255);
        color: white;
    }
    .server_image{
        padding-right: 10px;
        float: left;
    }
</style>