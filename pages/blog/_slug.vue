<template>
  <div>
    <nuxt-content :document="doc" />
  </div>
</template>
<script>
export default {
  layout: 'blog',
  async asyncData({ $content, params }) {
    const { slug } = params
    console.log(slug)
    const doc = await $content('/' + slug).fetch()
    return {
      doc,
    }
  },
}
</script>
<style></style>
