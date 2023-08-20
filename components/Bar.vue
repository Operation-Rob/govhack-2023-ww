<template>
    <div class="bg-lightpink flex items-center justify-center h-16">
      <!-- Logo Image -->
      <div class="logo-container mr-4">
        <img src="/image/logo.png" alt="Website Logo">
      </div>
      
      <!-- Website Title -->
      <h1 class="font-blackmango text-white">Wisdom Walks</h1>
    </div>
  </template>
  
  <style scoped>
  .bg-lightpink {
      background-color: #f4dbce;
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
  