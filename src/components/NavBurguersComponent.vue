<template>
    <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
        <a class="navbar-item mx-5" href="https://bulma.io">
        <img src="https://bulma.io/images/bulma-logo.png" width="112" height="28">
        </a>
    </div>

    <div id="navbarBasicExample" class="navbar-menu">
        <div class="navbar-end">
            <div class="navbar-item">
                <div class="buttons" id="nav">
                    <router-link to="/" class="mx-5 title is-4 " id="nav">Home </router-link>
                </div>
            </div>
        </div>
    </div>
</nav>


</template>

<script>
// import NewBurguerComponent from './NewBurguerComponent.vue';



export default{
    name: "NavBurguersComponent",
    props:['ShowHome'],
    data() {
        return {
        };
    },
    methods:{

    }

}

</script>