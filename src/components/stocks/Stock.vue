<template>
    <div class="col-sm-6 col-md-6">
        <div class="panel panel-success">
            <div class="panel-heading panel-success">
                <h3 class="panel-title">
                    {{stock.name}}
                    <small>(price: {{stock.price}})</small>
                </h3>
            </div>
            <div class="panel-body">
                <div class="pull-left">
                    <input type="number"
                    class="form-control"
                    placeholder="Quantity"
                    v-model.number="quantity">
                </div>
                <div class="pull-right">
                    <button 
                    class="btn btn-success"
                    @click="buyStock"
                    :disabled=" insuffientFunds || quantity <= 0 || !Number.isInteger(quantity)"
                    >{{insuffientFunds ? "insuffient Funds" : "Buy"}}</button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    props:['stock'],
    data(){
        return{
            quantity: 0
        }
    },
     computed:{
        funds(){
            return this.$store.getters.funds
        },
        insuffientFunds(){
            return this.quantity * this.stock.price > this.funds
        }
    },
    methods:{
        buyStock(){
            const order = {
                stockId: this.stock.id,
                stockPrice: this.stock.price,
                quantity: this.quantity
            };
            this.$store.dispatch('buyStock',order)
            this.quantity = 0;
        }
    },
   
}
</script>  