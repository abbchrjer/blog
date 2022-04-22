<template>
  <article class="grid grid-cols-12 pb-24 mt-8">
    <div class="flex w-full col-start-2 col-span-12">
      <div class="col-start-2 col-span-6 w-full">
        <div>
          <NuxtLink to="/home" href="/home" class="block text-gray-400 mt-8">← Go Back</NuxtLink>
          <h1 class="text-5xl font-black mt-2">{{ post.title }}</h1>
        </div>
        <nuxt-content class=" mt-4 prose max-w-none" :document="post" />
      </div>
    </div>
  </article>
</template>
<script>
export default {
  async asyncData({ $content }) {
    const post = await $content('about').fetch()

    return { post }
  }
}
</script>