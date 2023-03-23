<template>
    <div>
        <h1>
            Detalles de nuestras hamburguesas
        </h1>

        <!-- <div v-for="burguer of Burguers" v-bind:key="burguer.id">
            <h4>{{burguer.nombre}}</h4>
           <p class="card-text" v-for= "ingredient of burguer.ingredientes" v-bind:key="ingredient" >{{ingredient}}</p>
            <p>{{burguer.calorias }}</p> 
            <a href="#" class="btn btn-primary" >Button</a>
        </div> -->

    </div>
</template>

<script>
// const Burguers = ref(this.saludo);
export default {
    name: "ViewBurguers",
    data() {
        return {
            Burguers: []
        };
    },

    methods: {
        getBurguersData() {
            this.$http.get("https://hamburguesas-back.elevadev.cl/burger/").then(
                (response) => {
                    this.Burguers = response.data;
                },
                (err) => console.log(err)
            );
        },
    },
    created() {
        console.log("componente welcome creado!, llamando a api");
        this.getBurguersData();
    },
};
</script>

<style>
.welcome-component {
    padding: 10px;
    border: black 2px solid;
}

.hi {
    font-weight: bold;
    font-size: 1.5rem;
}
</style>
