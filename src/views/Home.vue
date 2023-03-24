<template>
  <div class="home">
    <NavBurguersComponent/>
    <img alt="Vue logo" src="../assets/logo.png">
    <WelcomeComponent :algo="unaVariable"/>
    <SliderHomeComponent/>
    
  </div>
  
</template>

<script>
// @ is an alias to /src
import WelcomeComponent from '@/components/WelcomeComponent.vue'
import NavBurguersComponent from '../components/NavBurguersComponent.vue';
import SliderHomeComponent from '../components/SliderHomeComponent.vue';

export default {
  name: 'Home',
  components: {
    WelcomeComponent,
    SliderHomeComponent,
    NavBurguersComponent
},
  data() {
    return {
      unaVariable: 'una cosa cualquiera'
    }
  }
}
</script>
