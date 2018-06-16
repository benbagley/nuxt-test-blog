<template>
  <nav class="flex items-center bg-green w-screen justify-between flex-wrap p-6">
    <section class="flex items-center flex-no-shrink mr-6">
      <nuxt-link to="/" class="block lg:inline-block text-white uppercase lg:mt-0 no-underline mr-4">Nuxt Test Blog</nuxt-link>
    </section>

    <section class="block lg:hidden">
      <button class="flex items-center p-2" @click="toggle">
        <i class="fal fa-bars text-white"></i>
      </button>
    </section>

    <section class="block text-left lg:flex w-full lg:items-center lg:w-auto lg:text-right" :class="open ? 'block': 'hidden'">
      <nuxt-link to="/posts" class="block mt-3 lg:inline-block text-white lg:mt-0 no-underline mr-4">Posts</nuxt-link>
      <nuxt-link to="/about" class="block mt-3 lg:inline-block text-white lg:mt-0 no-underline mr-4">About</nuxt-link>
      <nuxt-link to="/contact" class="inline-block text-sm px-4 py-2 leading-none text-white border border-green-dark bg-green-dark hover:bg-green-darker hover:border-green-darker rounded no-underline mt-4 mr-4 lg:mt-0">Contact</nuxt-link>
    </section>
  </nav>
</template>

<script>
export default {
  data: function () {
    return {
      open: false
    }
  },
  methods: {
    toggle() {
      this.open = !this.open
    }
  }
}
</script>
