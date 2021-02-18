<template>
  <div class="map">
    <div id="mapid">
    </div>
  </div>
  <div>
    <button class="btn btn-primary" @click="miCasa">Mi casa</button>
  </div>
</template>

<script>
import L from "leaflet"
import {onMounted} from "vue"

export default {

  setup(){
    let mymap

    function miCasa(){
      let marker = L.marker([40.40455639883969, -3.745392645022648]).addTo(mymap)
      marker.bindPopup("<b>Esta es mi casa</b>")
    }

    onMounted(()=>{
      mymap =  L.map(mapid).setView([40.4169420552663, -3.7033611530431543], 12)
      L.tileLayer('https://stamen-tiles-{s}.a.ssl.fastly.net/watercolor/{z}/{x}/{y}.{ext}', {
        attribution: 'Map tiles by <a href="http://stamen.com">Stamen Design</a>, <a href="http://creativecommons.org/licenses/by/3.0">CC BY 3.0</a> &mdash; Map data &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors',
        subdomains: 'abcd',
        minZoom: 1,
        maxZoom: 16,
        ext: 'jpg'
      }).addTo(mymap)
    })

    return{
      miCasa
    }
  }
}
</script>

<style lang="scss" scoped>
button{
  margin: 15px;
}
#mapid{
  height: 80vh;
}
</style>