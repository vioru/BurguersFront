<template>
  <div>
    <NavBurguersComponent/>
    <AllBurguersComponent />
    

    
  </div>
</template>

<script>
import AllBurguersComponent from "../components/AllBurguersComponent.vue";
import NavBurguersComponent from "../components/NavBurguersComponent.vue";



export default {
  name: "Burgers",
  components: {
    AllBurguersComponent,
    NavBurguersComponent,
}
};
</script>

<style>


</style>
