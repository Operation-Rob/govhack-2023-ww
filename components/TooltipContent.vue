<template>
  <div class="flex items-center">
    <div class="flex-shrink-0 w-14 h-14 border-2 p-0" style="border-color: #bfafa6;">
      <img
        class="object-fill w-full h-full"
        :src="`image/sites/${properties.image}`"
        alt="Site logo"
      />
    </div>
    <div class="ml-3">
      <!-- Adjusted the font size to `text-md` from `text-lg` -->
      <p class="text-md font-medium truncate" style="max-width: 300px; color: #bfafa6; font-family: 'Black Mango';">
        {{ properties.name }}
      </p>
      <div 
        @click="navigateToArticle" 
        class="flex justify-center items-center text-sm text-white hover:underline cursor-pointer py-1 px-3 rounded" 
        style="max-width: 300px; background-color: #bfafa6; font-family: 'Black Mango';"
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
