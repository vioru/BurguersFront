<template>
<div class="container content-menu">
    <div class="position-absolute m-3 ">
            <p class="has-text-white m-3 title is-4 text">Conoce nuestras Burguers,
            hechas con los mejores ingredientes</p>
            <router-link to="/hamburguesas" class="button is-success is-medium m-3 btn-menu">
                MENU
            </router-link>
    </div>
    <img alt="Vue logo" 
    src="https://crehana-blog.imgix.net/media/filer_public/6f/3e/6f3e8760-aeff-4b1c-baa3-85a05b95ea40/restaurantes-de-hamburguesas.png"
    class="slider-img" >
</div>


            
</template>

<script>
export default{
    name: "HomeMenuComponent",
    data() {
        return {

        };
    },
    methods: {

    },
    components: {  }
}
</script>

<style>



</style>