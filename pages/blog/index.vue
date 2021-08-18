<template>
  <div class="blog-container">
    <div v-for="(item, index) in articles" :key="index" class="blog-list">
      <div class="separator"></div>
      <div class="blog-title">{{ item.title }}</div>
      <div class="blog-description">{{ item.description }}</div>
      <nuxt-link :to="'/blog' + item.path" class="blog-read-all"
        >阅读全文</nuxt-link
      >
    </div>
  </div>
</template>
<script>
export default {
  async asyncData({ $content }) {
    const articles = await $content('/')
      .only(['title', 'description', 'path'])
      .fetch()
    return {
      articles,
    }
  },
}
</script>
<style>
.blog-container {
  width: 100%;
  height: 100%;
}
.blog-list {
  width: 100%;
  padding-bottom: 80px;
}

.separator {
  background: #18191b;
  width: 50px;
  height: 1px;
  border-radius: 10px;
}
.blog-title {
  width: 100%;
  color: #18191b;
  font-size: 20px;
  margin: 20px 0px;
}
.blog-description {
  width: 100%;
  margin: 20px 0px;
  display: -webkit-box;
  overflow: hidden;
  white-space: normal !important;
  text-overflow: ellipsis;
  word-wrap: break-word;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
}
.blog-read-all {
  color: #e94328;
  cursor: pointer;
  user-select: none;
}
</style>
