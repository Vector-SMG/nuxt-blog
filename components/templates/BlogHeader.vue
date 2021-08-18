<template lang="">
  <div class="blog-header-container">
    <div class="logo-container" @click="goHome()">
      <div class="logo">朝花夕拾</div>
    </div>
    <span class="back-btn" @click="goBack()">←</span>
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
<style>
.blog-header-container {
  width: 100%;
  position: fixed;
  background: white;
  z-index: 1000;
  padding: 80px 80px 40px 80px;
}
.logo-container {
  width: 100%;
  height: 50px;
  display: flex;
  justify-content: center;
}
.logo {
  font-weight: 700;
  font-size: 25px;
  height: 50px;
  display: flex;
  justify-content: center;
  writing-mode: vertical-rl;
  writing-mode: tb-lr;
  font-family: Geneva, Tahoma, Verdana, sans-serif;
  font-weight: 400;
  user-select: none;
  cursor: pointer;
  line-height: 28px;
  position: relative;
}
.back-btn {
  font-size: 30px;
  height: 50px;
  line-height: 50px;
  text-align: center;
  display: inline-block;
  color: #18191b;
  cursor: pointer;
}
</style>
