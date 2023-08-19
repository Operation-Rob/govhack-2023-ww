<template>
    <MapboxMarker :lng-lat="props.coordinates" @click="">
          <template v-slot:popup>
            <div class="flex">
              <div class="flex-shrink-0">
                <img
                  class="w-10 h-10 rounded-full"
                  :src="`@/assets/image/sites/${props.image}`"
                  alt="Site logo"
                />
              </div>
            </div>
          </template>
        </MapboxMarker>
    </template>

<script setup>
import { MapboxMarker } from '@studiometa/vue-mapbox-gl'

const props = defineProps({
  coordinates: {
    type: Array,
    required: true
  },
  description: {
    type: String,
    default: 'No description provided'
  },
  image: {
    type: String,
    default: ''
  }
})

</script>