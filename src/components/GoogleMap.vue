
<template>
  <gmap-map :center="center" :zoom="11" style="width: 100%; height: 500px">
    <gmap-marker
      v-model="markers"
      :key="index"
      v-for="(m, index) in markers"
      :position="m.position"
      :title="m.title"
      :clickable="true"
      :draggable="true"
      @click="center = m.position"
    ></gmap-marker>
  </gmap-map>
</template>
<script>
import axios from "axios";
import { gmapApi } from "vue2-google-maps";

export default {
  name: "GoogleMap",
  data() {
    return {
      center: { lat: this.latitude, lng: this.longitude },
      markers: [
        {
          position: { lat: this.latitude, lng: this.longitude },
          title: this.title
        },
      ],
    };
  },

  props: {
    latitude: Number,
    longitude: Number,
    title: String,
  },
  computed: {
    google: gmapApi,
  },
  methods: {
    setMarcadores() {

      axios
        .get("https://62df2213976ae7460be831a4.mockapi.io/marcadores")
        .then((response) => {
          // this.info = response;
          let marcadores = response.data;
          marcadores.forEach((element,index) => {
            let newMakerPosition = {
              position: {
                lat: Number(element.latitude),
                lng: Number(element.longitude),
              },
              title: "Teste Titulo "+index,
            };
            this.markers.push(newMakerPosition);
          });
        });
    },
    removeUm() {
        console.log(this.markers);
        console.log('tamanho: ' ,this.markers.length);
    },
  },
  created() {
    
    // aa
    this.setMarcadores();
    this.removeUm();
  },
};
</script>
