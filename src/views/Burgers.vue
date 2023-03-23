<template>
  <div>
    <h1>
        Conoce nuestras hamburguesas
      </h1>

    <div v-for="burguer of Burguers" v-bind:key="burguer.id" class="d-flex">
        <div class="row">
          <img alt="Vue logo" src="../assets/logo.png" width="50px">
          <h4 class="col-4" >{{burguer.nombre}}</h4>
          <a href="#" class="btn btn-primary col-4" >Button</a>
        </div>
        <!-- <ViewDetailsComponent :idBurguer="id" /> -->
    </div>
    
  </div>
</template>

<script>
// import ViewDetailsComponent from "../components/ViewDetailsComponent.vue";

export default {
  name: "Burgers",
  // components: {
  //   ViewDetailsComponent,
  // },
  data() {
    return {
      id: "pase info de prop",
      Burguers: [],
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
    }
};
</script>

<style></style>
