<template>
  <div>
    <h1>{{ article.title }}</h1>
    <p>{{ article.description }}</p>
    <nuxt-link :to="`/edit/${article.id}`">Edit Article</nuxt-link><br/>
    <img :src="`/image/sites/${article.image}`" alt="Article Image" />
  </div>
</template>

<script>
export default {
  async asyncData({ params }) {
    // Replace this with your actual data fetching method, e.g., axios.
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