<template>
    <div id="app" @click="closeWeChatIcon">
        <IrisnetMask></IrisnetMask>
        <IrisnetHeader></IrisnetHeader>
        <router-view/>
        <IrisnetFooter></IrisnetFooter>
        <float-window></float-window>
    </div>
</template>

<script>
    import IrisnetHeader from "./components/IrisnetHeader";
    import IrisnetFooter from "./components/IrisnetFooter";
    import IrisnetMask from "./components/IirsnetMask";
    import FloatWindow from "./components/FloatWindow";
    export default {
        name: 'app',
        components: {FloatWindow, IrisnetMask, IrisnetFooter, IrisnetHeader},
        data(){
            return{
            }
        },
        watch:{
            $route(){
                document.body.scrollTop = 0;
            }
        },
        mounted () {
         /*   const script = document.createElement('script');
            script.src = `https://s95.cnzz.com/z_stat.php?id=1278157493&web_id=1278157493`;
            script.language = 'JavaScript';
            document.body.appendChild(script)*/
        },
        methods: {
            closeWeChatIcon () {
                this.$store.commit('controlWeChat', false)
            }
        }
    }
</script>
<style lang="less">
  
    html {
        font-size: 625% !important;
        -webkit-text-size-adjust: none;
    }
    body{
        font-size:16px !important;
    }

    #app{
        width: 100%;
        background: rgba(13,14,44,1);
    }
    
    @import "assets/style/reset.less";
</style>

