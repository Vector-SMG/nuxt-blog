<template>
  <div class="blog-container">
    <BlogHeader />
    <nuxt class="blog-content" />
  </div>
</template>
<script>
export default {
  methods: {
    goHome() {
      this.$router.push({
        path: '/',
      })
    },
    goBack() {
      this.$router.go(-1)
    },
  },
}
</script>
<style scoped>
.blog-container {
  width: 100%;
  height: 100%;
}
.blog-content {
  height: calc(100% - 220px);
  width: 100%;
  padding: 220px 80px 20px 80px;
}
</style>
