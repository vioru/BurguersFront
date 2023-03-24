<template>
  <div>
    <NavBurguersComponent/>
      <h1 class="title">
        MENU
      </h1>
      <div  class="container">
          <div class="columns is-desktop is-mobile is-tablet is-multiline is-centered " >
            <AllBurguersComponent class="my-5"/>
          </div>
      </div>
    
  </div>
</template>

<script>
import AllBurguersComponent from "../components/AllBurguersComponent.vue";
import NavBurguersComponent from "../components/NavBurguersComponent.vue";



export default {
  name: "Burgers",
  components: {
    AllBurguersComponent,
    NavBurguersComponent
},
  data() {
    return {
      // Details: {},
      // Burguers: [],
      // showDetails: false,
      // id:"",
      // isActive:false,
    };
  }
  

};
</script>

<style>

</style>
