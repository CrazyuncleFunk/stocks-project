<template>
  <div class="container">
    <app-header></app-header>
    <div class="row">
      <div class="col-xs-12">
        <router-view></router-view>
      </div>
    </div>
   
  </div>
</template>

<script>
import Header from './components/Header'

export default {
  components:{
    appHeader: Header
  },
  created(){
    this.$store.dispatch('initStocks')
  }
  

}
</script>

<style>
body {
margin-top:30px;
}
</style>
