<template>

<nav class="navbar is-justify-content-space-between" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
        <a class="navbar-item" href="https://bulma.io">
        <img src="https://bulma.io/images/bulma-logo.png" alt="Bulma: Free, open source, and modern CSS framework based on Flexbox" width="112" height="28">
        </a>

        <router-link to="/" class=" title is-4 " id="nav">Home </router-link>

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