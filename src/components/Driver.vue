<template>
  <div>
    <h2>This is driver component</h2>
    <input type="text" v-model="location">
    <p>{{ location }}</p>


  <gmap-map
  :center="center"
  :zoom="7"
  style="width: 500px; height: 300px">
  <gmap-marker
    :key="index"
    v-for="(m, index) in markers"
    :position="m.position"
    :clickable="true"
    :draggable="true"
    @click="center=m.position"></gmap-marker>
  </gmap-map>
</div>
</template>

<script>
import * as VueGoogleMaps from 'vue2-google-maps';
import Vue from 'vue';
Vue.use(VueGoogleMaps, {
  load: {
    key: 'AIzaSyARXikf8fvb_SyWNSCBBOGkhz7NHHcMC5w',
    v: '3.28',
  }
});
  export default {
    data(){
      return {
        location: '',
        center: {lat: 10.0, lng: 10.0},
        markers: [{
          position: {lat: 10.0, lng: 10.0}
        }, {
          position: {lat: 11.0, lng: 11.0}
        }],
      }
    },

  }
</script>

<style>

</style>
