<template>
    <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
        <a class="navbar-item mx-5" href="https://bulma.io">
        <img src="https://bulma.io/images/bulma-logo.png" width="112" height="28">
        </a>
    </div>

    <div id="navbarBasicExample" class="navbar-menu">
            <div id="nav" >
                <router-link to="/" class="mx-5 title is-4">Home</router-link>

                <router-link to="/hamburguesas" class="mx-5 title is-4">Hamburguesas</router-link>
            </div>
    <router-view/>

        <div class="navbar-end">
        <div class="navbar-item">
            <div class="buttons">
                <NewBurguerComponent/>
            </div>
        </div>
        </div>
    </div>
</nav>


</template>

<script>
import NewBurguerComponent from './NewBurguerComponent.vue';



export default{
    name: "NavBurguersComponent",
    data() {
        return {};
    },
    components: { NewBurguerComponent }
}

</script>