<template>
  <section class="container flex flex-wrap">
    <PostPreview
      v-for="post in posts"
      :key="post.id"
      :id="post.id"
      :thumbnailImage="post.thumbnailURL"
      :title="post.title"
      :excerpt="post.previewText" />
  </section>
</template>

<script>
import PostPreview from '@/components/Post/PostPreview';

export default {
  components: {
    PostPreview
  },
  asyncData(context) {
    return context.app.$storyapi.get('cdn/stories', {
      version: process.env.NODE_ENV == 'production' ? 'published' : 'draft',
      starts_with: 'posts/'
    }).then(res => {
      return {
        posts: res.data.stories.map(bp => {
          return {
            id: bp.slug,
            title: bp.content.title,
            previewText: bp.content.excerpt,
            thumbnailURL: bp.content.thumbnail
          }
        })
      }
    })
  }
}
</script>
