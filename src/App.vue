<template>
  <div id="app">
    <div class="row">
      <h1 style="text-align: center">Proyecto Vue Google Map</h1>
      <button @click="setaNuloMap">Seta Null</button>
      <GoogleMap
        :latitude="-2.5453780416163627"
        :longitude="-44.2345619213127"
        :title="'Titulo Marcador'"
      />
    </div>
   
  </div>
</template>

<script>
import GoogleMap from "./components/GoogleMap.vue";
// import axios from "axios";


export default {
  name: "App",
  components: {
    GoogleMap,
  },
  methods: {
     setaNuloMap() {
      
    },
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
