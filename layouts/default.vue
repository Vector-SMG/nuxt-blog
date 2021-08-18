<template>
  <div class="default-container">
    <Header />
    <div class="content-container">
      <nuxt keep-alive />
    </div>
    <Bottom />
  </div>
</template>

<script>
export default {}
</script>

<style>
.default-container {
  width: 100%;
  height: 100%;
  box-sizing: border-box;
  background: white;
}
.default-container .content-container {
  height: calc(100% - 320px);
  width: 100%;
  padding: 240px 80px 80px 80px;
}
::-webkit-scrollbar {
  display: none;
}
</style>
