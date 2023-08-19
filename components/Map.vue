<template>
  <div>
    <div id="map"></div>
  </div>
</template>

<script>
  import mapboxgl from 'mapbox-gl'
  import dataset from '@/data/sites.json'

  export default {
    data() {
      return {
        access_token: process.env.MAPBOX_TOKEN,
        map:{}
      }
    },
    mounted() {
      this.createMap()
    },
    methods: {
      createMap() {
        mapboxgl.accessToken = this.access_token
        console.log(mapboxgl.accessToken)
        this.map = new mapboxgl.Map({
          container: 'map',
          style: 'mapbox://styles/cjnbennett/clli2gymn00jn01pr0i2s6xne',
          center: [143.36599431114507,-31.68953090523168],
          zoom: 6,
          maxZoom: 6,
          minZoom: 6,
          maxBounds: [140.5, -35.159189, 160.976835, -20.980645],
          dragPan: false,
          scrollZoom: false,
          touchZoomRotate: false
        })

        this.map.on('load', () => {
          this.map.addSource('sites', {
            type: 'geojson',
            data: dataset
          })
          this.map.addLayer({
            id: 'sites',
            type: 'circle',
            source: 'sites',
            paint: {
              'circle-color': '#4264fb',
              'circle-radius': 6,
              'circle-stroke-width': 2,
              'circle-stroke-color': '#ffffff'
            }
          })
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