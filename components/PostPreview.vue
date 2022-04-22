<template>
  <li class="transition-all duration-500 ease-in-out">
    <a :href="`/posts/${post.slug}`">
      <nuxt-img
        class=""
        :src="post.image"
        preset="preview"
        width="400"
        height="300"
      />
      <ul v-if="post.tags" class="flex space-x-3 mt-2">
        <li class="text-gray-400 font-bold" v-for="tag in post.tags" :key="tag">
          {{ tag }}
        </li>
      </ul>
      <h2 class="mt-2 text-3xl font-semibold">{{ post.title}}</h2>
      
      <h5 class="mt-5">{{post.description}}</h5>

      <div class=" flex space-x-3 space-y-3 flex-wrap justify-start text-sm items-end mt-5 font-bold">
        <div class="flex bg-sky-500 hover:bg-sky-600 transition duration-200 py-3 px-4 shadow-sm rounded-md cursor-pointer text-white text-bold">Read more
        </div>
      </div>
      <div class="border-b-2 border-grey-900 h-1 mt-8 mb-3"></div>
    </a>
  </li>
</template>
<script>
export default {
  props: {
    post: Object,
  }
}
</script>