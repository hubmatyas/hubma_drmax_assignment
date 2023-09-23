<script lang="ts">
import { defineComponent, PropType } from 'vue';

interface Article {
  id: number;
  title: string;
  url: string;
  time: number;
}

export default defineComponent({
  props: {
    article: {
      type: Object as PropType<Article>,
      required: true,
    },
   index: {
    type: Number,
    required: true,
  },
  },
  computed: {
    formattedTime() {
      return new Date(this.article.time * 1000).toLocaleString();
    },
  },
});
</script>

<template>
  <li>
    <article class="article">
       <div class="article-index">
        <span>
          {{ index + 1 }}.
        </span>
       </div>
		  <a class="article-title" :href="article.url" target="_blank" rel="nofollow">{{ article.title }} <sup>[ext]</sup></a>
      <span class="article-datetime">{{ formattedTime }}</span>
		  <a class="article-discussion" :href="'https://news.ycombinator.com/item?id=' + article.id">Rant 'bout it &raquo;</a>
	  </article>
  </li>
</template>

<style scoped>
.article {
  position: relative;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-template-areas: 
  "title title"
  "datetime discussion";
  gap: 2rem;
  background: #fff;
  border-radius: 1rem;
  color: #131313;
  padding: 1.8rem 2.4rem;
  height: 100%;
  align-items: flex-end;
  border: 0.1rem solid rgba(0,0,0,0.1);
}
.article-title {
  word-wrap: break-word;
  font-size: 1.8rem;
  font-weight: 700;
  line-height: 1.3;
  grid-area: title;
  grid-column: span 2;
  min-height: 2em;
}
.article-title sup {
  font-size: 0.65em;
}
.article-title:hover {
  text-decoration: underline;
}
.article-datetime {
  grid-area: datetime;
}
.article-discussion {
  display: block;
  width: max-content;
  max-width: 100%;
  height: max-content;
  padding: 0.2rem 1.8rem;
  line-height: 1.7;
  border-radius: 0.5rem;
  background: #757ccb;
  color: #fff;
  grid-area: discussion;
  font-weight: 700;
  justify-self: flex-end;
  transition: 0.3s ease-in-out;
  transform: scale(1);
}
.article-discussion:hover{
  background: #595f9b;
  transform: scale(1.1);
}
.article-index {
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
  inset: 0 auto auto 0;
  z-index: 2;
  background: #fff;
  transform: translate(-50%, -50%);
  border-radius: 50%;
  width: 2em;
  height: 2em;
  border: 0.1rem solid rgba(0,0,0,0.1);
}
.article-index span {
  display: block;
  line-height: 1.5;
  font-weight: 700;
}
@media only screen and (max-width: 660px) {
  .article {
    padding: 1.4rem 1.8rem;
    font-size: 0.8em;
  }
}
</style>