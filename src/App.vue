<template>
  <div>
    <ul>
      <li v-for="article in articles" :key="article.id">
        {{ article.title }} <br />
        {{ article.content }}
      </li>
    </ul>
    <button @click="Load">LoadA</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      articles: []
    };
  },

  async mounted() {
    this.load();
  },

  methods: {
    async load() {
      const response = await axios.get("http://localhost:3000/articles");
      this.articles = response.data;
    }
  }
};
</script>
