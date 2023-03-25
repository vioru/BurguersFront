<template>
    <div>
        <div  class="container">
            <NewBurguerComponent class="boton" @reload="getBurguersData"/>
            <h1 class="title"> MENU </h1>
            <div class="columns is-desktop is-mobile is-tablet is-multiline is-centered " >
                <div class="column is-12-mobile is-4-desktop is-6-tablet" v-for="burguer of Burguers" v-bind:key="burguer.id">
                <div class="card">
                    <div class="card-header d-flex justify-content-center">
                    <img alt="foto producto" src="https://bakeitwithlove.com/wp-content/uploads/2022/01/what-to-serve-with-burgers-sq.jpg" class="image is-256x256">
                    </div>
                    <div class="card-content">
                    <h4 class="title is-size-4">{{ burguer.nombre.toUpperCase() }}</h4>
                    <button class="button is-danger is-rounded is-responsive  align-self-center "
                    v-on:click="FilterId(burguer.id)" id="openModal">
                        Borrar
                    </button> 
                    
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
                            <template v-if="filtereds" > 
                                <p>¿Estas Seguro que deseas borrar?</p>
                                <button  class="button is-danger m-5" id="btncancle" 
                            v-on:click="DeleteBurguer()"> Borrar</button>
                            
                            </template>
                            <div v-else>
                                <ViewDetailsComponent  :oneBurguer="Details" class="is-justify-content-center is-align-items-center" />
                            </div>
                            
                        </section>
                        <footer  class="modal-card-foot  is-justify-content-center">
                            <button  class="button" id="btncancle" 
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
import NewBurguerComponent from "./NewBurguerComponent.vue";


export default {
    name: "AllBurgersComponent",
    components: {
    ViewDetailsComponent,
    NewBurguerComponent
},

    data() {
        return {
        filtereds:[],
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
            this.openModal();
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
        this.filtereds = []
        },
        openModal(){
            this.isActive = true
            this.filtereds = ""
        },
        FilterId(BurguerId){
            this.sendId();
            console.log("soly el id",BurguerId);
            this.filtereds = BurguerId;
            this.isActive = true
        },
        DeleteBurguer(){
            this.Burguers = this.Burguers.filter(word => word.id != this.filtereds);
            this.isActive = false
        }
        
    },
    created() {
        console.log("componente welcome creado!, llamando a api");
        this.getBurguersData();
    },
    

};
</script>

<style>
</style>