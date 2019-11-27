<template>
    <div>
        <h1>Trade or view Portfolio</h1>
        <h2>You may Save and Load your data</h2>
        <h2>Click End Day to progress to the next day.</h2>
        <hr>
        <p>Your Funds: {{funds}}</p>
    </div>
</template>
<script>
    export default {
        computed:{
            funds(){
                return this.$store.getters.funds
            }
        }
    }
</script>
<style scoped>
h2{
    font-size:2rem;
}
</style>