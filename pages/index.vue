<template>
  <div id="app">
    <Header />
    <main class="container">
      <Hero />
      <div class="row mb-2">
        <Article
          v-for="article in articles"
          :key="article.link"
          :article="article"
        />
      </div>
    </main>
  </div>
</template>

<script>
import Header from '../components/Header.vue'
import Hero from '../components/Hero.vue'
import Article from '../components/CardArticle.vue'
export default {
  data() {
    return {
      articles: [],
    }
  },
  components: {
    Header,
    Hero,
    Article,
  },
  async fetch() {
    await this.$axios.get('v1/cnn-news').then((res) => {
      this.articles = res.data.data
      console.log('Artikel =>', this.articles)
    })
  },
}
</script>
<style></style>
