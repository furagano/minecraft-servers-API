<template>
    <div class="server" v-for="server in servers" :key="server.favicon_base64">
        <template v-if="server.error">
            <div>not found 404</div>
        </template>
        <template v-else>
            <div><strong>Название:</strong> {{server.description.replace(/§\w/g,'')}} </div>
            <div><strong>Онлайн:</strong> {{server.players.online}} </div>
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
            default: 'mc.hypixel.net'
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
        margin-top: 15px;
        background-color: rgb(92, 241, 92);
        padding: 15px;
        border: 2px solid saddlebrown;
        border-radius: 12px;
        box-shadow:inset 0 -6em 6em rgba(0, 0, 0, 0.2),
        0.3em 1em 1em rgba(0, 0, 0, 0.3);
    }
</style>