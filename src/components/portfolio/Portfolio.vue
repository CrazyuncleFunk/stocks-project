<template>
    <div>
        <app-stock v-for="(stock,id) in stocks" :key="id" :stock="stock"></app-stock>
    </div>
</template>
<script>
import {mapGetters} from 'vuex';
import Stock from './Stock.vue';

    export default{
        computed:{
            ...mapGetters({
                stocks: 'stockPortfolio'
            })
        },
        components:{
            appStock: Stock
        }
    }
</script>