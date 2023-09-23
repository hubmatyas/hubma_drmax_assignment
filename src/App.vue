<script lang="ts" setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import Articles from './components/Articles.vue';
import Spinner from './components/Spinner.vue';

interface Article {
  id: number;
  title: string;
  url: string;
  time: number;
}

const topStories = ref<Article[]>([]);
const isLoading = ref(true);

const fetchTopStories = async () => {
  isLoading.value = true;

  const { data: top100Ids } = await axios.get<number[]>('https://hacker-news.firebaseio.com/v0/topstories.json?print=pretty');
  const promises = top100Ids.slice(0, 100).map(id => axios.get<Article>(`https://hacker-news.firebaseio.com/v0/item/${id}.json?print=pretty`));
  const responses = await Promise.all(promises);

  topStories.value = responses.map(res => res.data);

  isLoading.value = false;
};

onMounted(fetchTopStories);
</script>

<template>
  <div id="app">
    <header>
      <div class="wrapper">
        <h1 class="title">
          Top 100&nbsp;Hackernews articles
        </h1>
      </div>
    </header>
      <main>
          <section>
              <div class="wrapper">
                  <Articles :articles="topStories" />
                  <Spinner v-if="isLoading" />
              </div>
          </section>
      </main>
  </div>
</template>

<style scoped>
.title {
  text-align: center;
  font-size: 4.6rem;
  font-weight: 700;
}
</style>