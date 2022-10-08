<template>
    <div class="server" v-for="server in servers">
        <div><strong>Название:</strong> {{server.name}} </div>
        <div><strong>Онлайн:</strong> {{server.online}} </div>
        <div><strong>IP:</strong> {{server.ip}} </div>
    </div>
</template>
<script>
export default {
    data(){
        return {
          servers:[
            {id:1, name: 'hypixel', online: '50', ip: '214037598623875'},
            {id:2, name: 'hypixel 2', online: '50', ip: '214037598623875'},
        ]  
        }
        
    },
    methods(){
        
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