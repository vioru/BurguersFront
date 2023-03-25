<template>
    <div class="d-flex" >
        <img alt="Vue logo" src="https://bakeitwithlove.com/wp-content/uploads/2022/01/what-to-serve-with-burgers-sq.jpg" class="image is-128x128  ">
        <div>
            <h1 class="text-center is-size-2 is-uppercase" >
            {{oneBurguer.nombre }}
        </h1>
        <b>Ingredientes:</b>
        <ul>
            <li v-for="ingredient of oneBurguer.ingredientes" v-bind:key="ingredient">{{ingredient }}</li>
        </ul>
        <p><b>Calorias:</b>{{oneBurguer.calorias }}</p>
        </div>

        
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
