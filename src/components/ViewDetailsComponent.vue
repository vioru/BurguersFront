<template>
    <div >
        <h1 class="text-center is-size-2 is-uppercase" >
            {{oneBurguer.nombre }}
        </h1>
        <p v-for="ingredient of oneBurguer.ingredientes" v-bind:key="ingredient"><b>Ingredientes:</b>{{ingredient }}</p>
        <p><b>Calorias:</b>{{oneBurguer.calorias }}</p>
        
    </div>
</template>

<script>

export default {
    name: "ViewDetailsComponent",
    props: ['oneBurguer'],
    data() {
        return {
            Burguer: {},
            
        };
        
    },


};
</script>

<style>

</style>
