<template>
  <div class="home">
    <div class="is-desktop is-mobile is-tablet is-multiline ">
    <NavBurguersComponent  />
    </div>
    <HomeMenuComponent />
    <!-- <WelcomeComponent :algo="unaVariable"/> -->
  </div>
  
</template>

<script>
// @ is an alias to /src
// import WelcomeComponent from '@/components/WelcomeComponent.vue'
import NavBurguersComponent from '../components/NavBurguersComponent.vue';
import HomeMenuComponent from '../components/HomeMenuComponent.vue';

export default {
  name: 'Home',
  components: {
    // WelcomeComponent,
    HomeMenuComponent,
    NavBurguersComponent
},
  data() {
    return {
      unaVariable: 'una cosa cualquiera',
      HomeActivated:false,

    }


  }
  ,

}
</script>
