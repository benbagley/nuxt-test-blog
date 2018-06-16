<template>
  <div v-editable="blok">
    <section class="w-full bg-cover bg-center post-image" :style="{ backgroundImage: 'url(' + image + ')' }"></section>
    <section class="container p-4">
      <h1 class="text-grey=darker">{{ title }}</h1>
      <p class="text-grey-dark mt-4 whitespace-pre-wrap">{{ content }}</p>
    </section>
  </div>
</template>


<script>
export default {
  asyncData(context) {
    return context.app.$storyapi.get('cdn/stories/posts/' + context.params.postId, {
      version: context.isDev ? 'draft' : 'published'
    }).then(res => {
      return {
        blok: res.data.story.content,
        image: res.data.story.content.thumbnail,
        title: res.data.story.content.title,
        content: res.data.story.content.content
      }
    })
  },
  mounted() {
    this.$storyblok.init()
    this.$storyblok.on('change', () => {
      location.reload(true)
    })
  }
}
</script>

<style scoped>
  .post-image { height: 600px; }
</style>
