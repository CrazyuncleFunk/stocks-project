<template>
    <div class="col-sm-6 col-md-6">
        <div class="panel panel-primary">
            <div class="panel-heading panel-success">
                <h3 class="panel-title">
                    {{stock.name}}
                    <small>(price: {{stock.price}}) | Quantity {{stock.quantity}}</small>
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
                    class="btn btn-primary"
                    @click="sellStock"
                    :disabled="quantity <= 0 || !Number.isInteger(quantity)"
                    >Sell</button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import {mapActions} from 'vuex';
export default {
    props:['stock'],
    data(){
        return{
            quantity: 0
        }
    },
    methods:{
        ...mapActions({
            placeSellOrder:'sellStock'
        }),
       sellStock(){
           
           const order = {
               stockId: this.stock.id,
               stockPrice: this.stock.price,
               quantity: this.quantity
           };
           this.placeSellOrder(order);
           this.quantity = 0;

       }
    }
}
</script>  