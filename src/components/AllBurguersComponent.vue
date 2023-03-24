<template>
    <div>
        <div  class="container">
            <div class="columns is-desktop is-mobile is-tablet is-multiline is-centered " >
                <div class="column is-12-mobile is-4-desktop is-6-tablet" v-for="burguer of Burguers" v-bind:key="burguer.id">
                <div class="card">
                    <div class="card-header d-flex justify-content-center">
                    <img alt="Vue logo" :src="burguer.id/2 ? 'https://assets.stickpng.com/images/580b57fcd9996e24bc43c1a8.png':
                    'https://www.pngfind.com/pngs/m/426-4269881_hamburguesa-png-transparent-png.png' " class="image is-256x256 ">
                    </div>
                    <div class="card-content">
                    <h4 class="title is-size-4">{{ burguer.nombre.toUpperCase() }}</h4>
                    <button class="button is-success is-rounded is-responsive  align-self-center "
                    v-on:click="sendId(burguer.id)" id="openModal">
                        Ver Detalles
                    </button>
                    </div>
                </div>
            </div>
            <div :class="isActive ? 'modal is-active':'modal' " >
                <div class="modal-background"></div>
                    <div class="modal-card">
                        <header class="modal-card-head  flex-row-reverse">
                            <button class="delete" aria-label="close" id="btnclose  "
                            v-on:click="closeModal()"
                            ></button>
                        </header>
                        <section class="modal-card-body text-center">
                            <ViewDetailsComponent :oneBurguer="Details" class="is-justify-content-center is-align-items-center"/>
                        </section>
                        <footer class="modal-card-foot  is-justify-content-center">
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
    name: "AllBurgersComponent",
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
        },
        
    },
    created() {
        console.log("componente welcome creado!, llamando a api");
        this.getBurguersData();
    },
    

};
</script>

<style>




</style>