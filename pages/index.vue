<template>
  <div>
    <div id="map"></div>
  </div>
</template>

<script>
  import mapboxgl from 'mapbox-gl'

  export default {
    data() {
      return {
        map:{}
      }
    },
    mounted() {
      this.createMap()
    },
    methods: {
      createMap() {
        mapboxgl.accessToken = process.env.MAPBOX_TOKEN
        console.log(mapboxgl.accessToken)
        this.map = new mapboxgl.Map({
          container: 'map',
          style: 'mapbox://styles/mapbox/satellite-v9',
          zoom: 11,
          center: [107.61861, -6.90389]
        })
      }
    }
  }
</script>

<style scoped>
#map {
  width: 100%;
  height: 100vh;
}
</style>