<template>
  <div>
    <div id="map"></div>
  </div>
</template>

<script>
  import mapboxgl from 'mapbox-gl'
  import dataset from '@/data/sites.json'
  import { nextTick, h } from 'vue'
  import Vue from 'vue'
  import TooltipContent from '@/components/TooltipContent.vue'

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
        })

        this.map.on('load', () => {

// 1. Add an image to your map's style.
this.map.loadImage('/image/pin.png', (error, image) => {
    if (error) throw error;

    this.map.addImage('location-pin', image);

    // Add the geojson data source
    this.map.addSource('sites', {
        type: 'geojson',
        data: dataset
    });

    // 2. Use this image in a layer of type 'symbol'.
    this.map.addLayer({
        id: 'sites',
        type: 'symbol',
        source: 'sites',
        layout: {
            'icon-image': 'location-pin', // reference the image you just added
            'icon-size': 0.3 // adjust the size of the icon as needed
        },
        paint: {
            'icon-color': '#ec919c'
        }
    });
});
});

        const popup = new mapboxgl.Popup({
        closeButton: false,
        closeOnClick: false
      });

      this.map.on('mouseenter', 'sites', (e) => {
        this.map.getCanvas().style.cursor = 'pointer';

        // Copy coordinates array.
        const coordinates = e.features[0].geometry.coordinates.slice();
        const properties = e.features[0].properties;

        while (Math.abs(e.lngLat.lng - coordinates[0]) > 180) {
          coordinates[0] += e.lngLat.lng > coordinates[0] ? 360 : -360;
        }

        console.log(coordinates)
        popup.setLngLat(coordinates).setHTML('<div id="popup-content"></div>').addTo(this.map);

        nextTick(() => {
  const popupComp = new Vue({
    render: h => h(TooltipContent, { props: { properties } })
  }).$mount();  // This creates a new Vue instance and mounts it

  const popupEl = document.getElementById("popup-content");
  popupEl.appendChild(popupComp.$el);  // Appending the rendered component to the popup
});
      });

      this.map.on('mouseleave', 'sites', () => {
        this.map.getCanvas().style.cursor = '';
        setTimeout(() => {
        popup.remove();
    }, 3000);
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