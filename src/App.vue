<template>
  <!-- <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/hamburguesas">Hamburguesas</router-link>
  </div> -->
  <router-view/> 
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

.slider-img{
    width: 100%;
    height: 450px;
    object-fit: cover;
}

.text{
    text-shadow: 2px 2px 2px black;
}
.content-menu{
    display: flex;
    justify-content: center;
    align-items: center;
}
.btn-menu{
    box-shadow: 0px 5px  rgba(0, 0, 0, 0.89);
}

.boton{
    display: flex;
    justify-content: end;
    align-items: end;
}

</style>
