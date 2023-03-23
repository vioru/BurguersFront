<template>
  <div>
    <h1>
      Conoce nuestras hamburguesas
    </h1>
    <div  class="container">
      <div class="columns is-desktop is-mobile is-tablet is-multiline is-centered " >
          <div class="column is-12-mobile is-4-desktop is-4-tablet" v-for="burguer of Burguers" v-bind:key="burguer.id">
            <div class="card">
              <div class="card-header d-flex justify-content-center">
                <img alt="Vue logo" src="../assets/logo.png"  class="image is-256x256 ">
              </div>
              <div class="card-content">
                <h4 class="title is-size-4">{{ burguer.nombre.toUpperCase() }}</h4>
                <button class="button is-success is-rounded is-responsive col-sm-3 align-self-center "
                v-on:click="sendId(burguer.id)" id="openModal">
                  Ver Detalles
                </button>
              </div>
            </div>
          </div>

          <div :class="isActive ? 'modal is-active':'modal' " >
            <div class="modal-background"></div>
            <div class="modal-card">
                <header class="modal-card-head d-flex flex-row-reverse">
                    <button class="delete" aria-label="close" id="btnclose  "
                    v-on:click="closeModal()"
                    ></button>
                </header>
                <section class="modal-card-body text-center">
                  <ViewDetailsComponent :oneBurguer="Details" class=""/>
                </section>
                <footer class="modal-card-foot">
                    <button class="button is-success">Editar Información</button>
                    <button class="button" id="btncancle" 
                    v-on:click="closeModal()">Cerrar</button>
                </footer>
            </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ViewDetailsComponent from "../components/ViewDetailsComponent.vue";

export default {
  name: "Burgers",
  components: {
    ViewDetailsComponent,
  },
  data() {
    return {
      Details: {},
      Burguers: [],
      showDetails: false,
      id:"",
      isActive:false,
    };
  },
  methods: {

    sendId(idB) {
      this.id=idB
      console.log(this.id);
      this.$http.get("https://hamburguesas-back.elevadev.cl/burger/"+this.id).then(
        (response) => {
          this.Details = response.data;
          this.isActive = true
          console.log(this.isActive);
        },
        (err) => console.log(err)
      );
    },
    getBurguersData() {
      this.$http.get("https://hamburguesas-back.elevadev.cl/burger/").then(
        (response) => {
          this.Burguers = response.data;
          

        },
        (err) => console.log(err)
      );
    },
    closeModal(){
      this.isActive = false
    }
    
  },
  created() {
    console.log("componente welcome creado!, llamando a api");
    this.getBurguersData();
  },
  

};
</script>

<style></style>
