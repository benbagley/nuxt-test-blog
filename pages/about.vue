<template>
  <section class="container p-4" v-editable="blok">
    <h1 class="text-grey=darker">{{ title }}</h1>
    <p class="text-grey-dark mt-4 whitespace-pre-wrap">{{ content }}</p>
  </section>
</template>

<script>
export default {
  asyncData(context) {
    return context.app.$storyapi.get('cdn/stories/about', {
      version: context.isDev ? 'draft' : 'published'
    }).then(res => {
      return {
        blok: res.data.story.content,
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
