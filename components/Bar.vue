<template>
    <div class="bg-lightpink flex justify-between items-center h-16 p-4"> <!-- Added padding for some space -->
      
      <!-- Left side: Logo and Title -->
      <div class="flex items-center">
        <!-- Logo Image -->
        <div class="logo-container mr-4">
          <img src="/image/logo.png" alt="Website Logo">
        </div>
        
        <!-- Website Title -->
        <h1 class="font-blackmango text-white">Wisdom Walks</h1>
      </div>
  
      <!-- Right side: Button -->
      <button @click="navigateToNew" class="bg-darkpink text-white py-2 px-4 rounded font-blackmango">
        Create Article
      </button>
      
    </div>
  </template>

<script>
export default {
  methods: {
    navigateToNew() {
      const articleUrl = `/newarticle`;
      window.location.href = articleUrl;
    }
  }
}
</script>
  
  
  <style scoped>
  .bg-lightpink {
      background-color: #f4dbce;
  }

  .bg-darkpink {
      background-color: #ec919c;
  }
  
  .font-blackmango {
      font-family: 'Black Mango';
  }
  
  .logo-container {
      width: 48px;
      height: 48px;
      overflow: hidden;  /* in case the image is larger than the container */
  }
  
  .logo-container img {
      max-width: 100%;
      max-height: 100%;
      display: block;  /* removes any gap under the image */
  }
  </style>
  