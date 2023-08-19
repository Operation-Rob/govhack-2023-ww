<template>
    <div>
      <h2>Edit: {{ article.title }}</h2>
      <!-- Your editing form and controls go here -->
    </div>
  </template>
  
  <script>
  export default {
    async asyncData({ params }) {
      // This is a simple representation. In a real-world scenario, you'd fetch the article data from an API or database.
      const articles = {
        '1': {
          title: 'Sample Article 1',
          description: 'Description for article 1',
          image: 'montague-island.jpg'
        },
        '2': {
          title: 'Sample Article 2',
          description: 'Description for article 2',
          image: 'montague-island.jpg'
        }
      };
  
      return {
        article: articles[params.id] || {}
      };
    }
  }
  </script>  