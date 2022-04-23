<template>
<div>
  <article class="grid grid-cols-12 pb-24 mt-8">
    <nuxt-img
      class="col-start-3 col-span-8 w-full"
      :src="post.image"
      width="768"
      height="509"
    />
    <div class="w-full col-start-1 col-span-12 grid grid-cols-12">
      <!-- <nav > -->
         <!-- class="mt-8 col-span-2 shadow-2xl rounded-lg p-4 self-start" -->
        <!-- <ul class="space-y-2"> -->
          <!-- <li v-for="link of post.toc" :key="link.id">
            <NuxtLink
              class="uppercase tracking-wider text-gray-500 hover:underline"
              :to="`#${link.id}`"
              >{{ link.text }}</NuxtLink>
            >
          </li> -->
        <!-- </ul> -->
      <!-- </nav> -->
      <div class="col-start-4 col-span-6 w-full">
        <div>
          <NuxtLink to="/home" href="/home" class="block text-gray-400 mt-8">← To Posts</NuxtLink>
          <ul v-if="post.tags" class="flex space-x-3 mt-2">
            <li
              class="text-gray-400 font-bold"
              v-for="tag in post.tags"
              :key="tag"
            >
              {{ tag }}
            </li>
          </ul>
          <h1 class="text-5xl font-black mt-2">{{ post.title }}</h1>
        </div>

        <div class="text-sm mt-5 text-gray-400">

              <span>{{formatDate(post.updatedAt)}}</span>
          </div>

        <nuxt-content class="mt-4 prose max-w-none" :document="post" />
      </div>
    </div>
  </article>
  <prev-next :prev="prev" :next="next"></prev-next>
</div>
</template>

<script>

export default {
  async asyncData({ $content, params }) {
    const post = await $content('articles', params.slug).fetch()

    const [prev, next] = await $content('articles')
      .only(['title', 'slug', 'updatedAt'])
      .sortBy('updatedAt', 'asc')
      .surround(params.slug)
      .fetch()

    return { prev, next, post }

  },

      methods: {
        formatDate(date){
            return new Date(date).toLocaleDateString('en', {year: 'numeric', month: 'long', day: 'numeric'})
        }
    },


  head() {
    return {
      title: this.post.title,
      meta: [
        { hid: 'og:title', property: 'og:title', content: this.post.title },
        { hid: 'og:type', property: 'og:type', content: 'article' },
        {
          hid: 'og:image',
          property: 'og:image',
          content: `http://localhost:3000/${this.post.image}`,
        },
        {
          hid: 'twitter:title',
          name: 'twitter:title',
          content: this.post.title,
        },
        {
          hid: 'twitter:card',
          name: 'twitter:card',
          content: 'summary_large_image',
        },
        {
          hid: 'twitter:image',
          name: 'twitter:image',
          content: `http://localhost:3000/${this.post.image}`,
        }
      ]
    }
}
}
</script>