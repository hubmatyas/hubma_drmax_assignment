<script lang="ts">
import { defineComponent, PropType } from 'vue';
import Article from './Article.vue';

interface Article {
  id: number;
  title: string;
  url: string;
  time: number;
}

export default defineComponent({
  components: { Article },
  props: {
    articles: {
      type: Array as PropType<Article[]>,
      required: true,
    },
  },
});
</script>

<template>
  <ul class="article-list">
    <Article
      v-for="(article, index) in articles"
      :key="article.id"
      :article="article"
      :index="index"
    />
  </ul>
</template>

<style scoped>
.article-list {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  align-items: stretch;
  justify-content: stretch;
  gap: 3rem;
}
</style>