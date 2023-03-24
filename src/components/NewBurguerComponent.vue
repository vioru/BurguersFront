<template>

    <div>
        <button class="button is-success is-rounded is-responsive is-medium  " v-on:click="OpenModal()">   
                Crear Nueva Hamburguesa
        </button>
        <div :class="isActive ? 'modal is-active ':'modal' " >
                <div class="modal-background ">
                    <div class="modal-card my-5 ">
                        <header class="modal-card-head d-flex flex-row-reverse">
                            <button class="delete" aria-label="close" id="btnclose  "
                            v-on:click="closeModal()"
                            ></button>
                        </header>
                        <section class="modal-card-body text-center">
                            <form>
                                <div class="field">
                                    <label class="label">Dale un nombre a tu hamburguesa</label>
                                    <div class="control">
                                        <input class="input" type="text" placeholder="Pepa Burguer" name="nombre" id="nombre" v-model="form.nombre">
                                    </div> 
                                    <span className="text-danger"> {{ nombreError }} </span>
                                </div>
                                <div class="field">
                                <label class="label">Agrega los ingredientes</label>
                                <div class="control">
                                    <p>Nota:Ingresa tus ingredientes separados por coma</p>
                                    <textarea class="textarea" placeholder="Ingresa tus ingredientes separados por coma " name="ingredientes" id="ingredientes" v-model="form.ingredientes">
                                    </textarea>
                                </div>
                                <span className="text-danger"> {{ ingredientesError }}</span>
                                </div>
                                <div class="field">
                                    <label class="label">¿Cuantas calorias tiene?</label>
                                    <div class="control">
                                        <input class="input" type="number" name="calorias" id="calorias" v-model="form.calorias">
                                    </div>
                                    <span className="text-danger"> {{ caloriasError }}</span>
                                </div>

                                <div class="control">
                                    <button type="button" class="button is-primary" v-on:click="CreateBurguer()" >Guardar</button>
                                    <button class="button" id="btncancle" 
                                    v-on:click="closeModal()">Cancelar</button>
                                </div>
                            </form>
                            
                        </section>

                    </div>
                </div>
            </div>
                
    </div>
</template>

<script>


export default{
    name: "NewBurguerComponent",
    data() {
        return {
            isActive: false,
            form:{
                "nombre":"",
                "ingredientes":[""],
                "calorias":""
            },
            nombreError:"",
            ingredientesError:"",
            caloriasError:""
        };
    },
    methods: {
        OpenModal(){
            this.isActive = true;
            console.log(this.form);
            this.nombreError = "";
            this.ingredientesError = "";
            this.caloriasError = "";
        },
        CreateBurguer() {
            
            console.log(this.form.ingredientes.length)
            if(this.form.ingredientes.length >1){
                this.form.ingredientes= this.form.ingredientes.split(",");}
            else{this.form.ingredientes = ""}
            
            this.$http.post("https://hamburguesas-back.elevadev.cl/burger/",this.form).then(
            (response) => {
            console.log(response.data);
            this.isActive = false;
            this.$emit('reload')
            this.form.nombre = "";
            this.form.ingredientes = [""];
            this.form.calorias = "";
            },
            (err) =>{ console.log(err)
            if(err.response.data.nombre){
                this.nombreError = err.response.data.nombre[0];
            }
            if(err.response.data.ingredientes){
            this.ingredientesError = err.response.data.ingredientes[0];
            }
            if(err.response.data.calorias){
                this.caloriasError = err.response.data.calorias[0];
            }
            
        }
        );
        },
        closeModal() {
            this.isActive = false;
            
        },
        sendInfo(id){
                console.log(id);
        },
        guardar(){
            console.log(this.form2);
        },

    },

    components: {  }
}

</script>