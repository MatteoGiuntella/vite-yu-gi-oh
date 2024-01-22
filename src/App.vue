<script>
import AppHeader from './components/AppHeader.vue';
import Charger from './components/Charger.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';
import axios from 'axios';
import {store} from './store.js'
export default {
    data() {
        return {
            store,
            flag : true
        };
    },
    components: {
        AppHeader,
        AppMain,
        AppFooter,
        Charger
    },  
    methods: {

    },
    created(){
        setTimeout(() => {
            this.flag = false
        }, 3000);
    },
    mounted(){
        axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0').then((response) =>{
            console.log(response)
        this.store.listCard = response.data.data
        });
    }
}
</script>

<template>
    <Charger v-if="flag" />
    <AppHeader v-if="flag == false" />
    <AppMain v-if="flag == false"/>
    <AppFooter v-if="flag == false"/>
</template>

<style lang="scss">
@use "assets/scss/main" as *;
</style>
