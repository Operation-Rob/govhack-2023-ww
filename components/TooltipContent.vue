<template>
    <div class="flex items-center">
      <div class="flex-shrink-0">
      </div>
      <div class="ml-3">
        <p class="text-lg font-medium text-gray-900">
          {{ props.properties.name }}
        </p>
      </div>
    </div>
  </template>
  
  <script setup>
  const props = defineProps({
    properties: { required: true }
  })
  </script>