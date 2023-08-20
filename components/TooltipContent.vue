<template>
  <div class="flex items-center">
    <div class="flex-shrink-0 w-14 h-14 bg-gray-200 rounded-full overflow-hidden">
      <img
        class="object-fill w-full h-full"
        :src="`image/sites/${properties.image}`"
        alt="Site logo"
      />
    </div>
    <div class="ml-3">
      <p class="text-lg font-medium text-gray-900 truncate" style="max-width: 200px;">
        {{ properties.name }}
      </p>
      <div 
        @click="navigateToArticle" 
        class="text-sm text-gray-600 hover:underline cursor-pointer" 
        style="max-width: 200px;"
      >
        View article
      </div>
    </div>
  </div>
</template>
  
<script>
export default {
  props: {
    properties: {
      type: Object,
      required: true
    }
  },
  methods: {
    navigateToArticle() {
      const articleUrl = `/article/${this.properties.id}`;
      window.location.href = articleUrl;
    }
  }
}
</script>
