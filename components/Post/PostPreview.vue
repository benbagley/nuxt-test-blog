<template>
  <section class="w-full sm:w-1/2 py-4 px-4">
    <section class="rounded overflow-hidden shadow">
      <section class="w-full bg-cover bg-center h-64" :style="{ backgroundImage: 'url(' + thumbnailImage + ')' }"></section>
      <section class="px-6 py-4">
        <section class="font-bold text-xl mb-2">{{ title }}</section>
        <p class="text-grey-darker text-base">
          {{ excerpt }}
        </p>
      </section>
      <section class="px-4 py-4 float-right">
        <nuxt-link :to="/posts/ + id">
          <span class="inline-block px-3 py-1 text-sm font-semibold text-grey-darker">View More
            <i class="fal fa-arrow-right ml-2"></i>
          </span>
        </nuxt-link>
      </section>
    </section>
  </section>
</template>

<script>
export default {
  props: {
    id: {
      type: String,
      required: true
    },
    title: {
      type: String,
      required: true
    },
    excerpt: {
      type: String,
      required: true
    },
    thumbnailImage: {
      type: String,
      required: true
    }
  }
}
</script>
