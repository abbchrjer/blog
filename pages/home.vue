<template>
<div>
 <div class= "w-full h-full bg-no-repeat bg-cover bg-left bg-fixed" style="background-image: url(/images/food.jpg)">
  </div>
  <div>
    <ul class="grid flex md:grid-cols-2 md:gap-4 xs:grid-cols-1 lg:grid-cols-3 lg:gap-8 m-8">
      <PostPreview v-for="post in posts" :key="post.slug" :post="post"></PostPreview>
    </ul>
  </div>

</div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const posts = await $content('articles')
      .only(['title', 'image', 'tags', 'slug', 'description', 'updatedAt'])
      .sortBy('createdAt', 'desc')
      .fetch()
      
    return {
      posts,
    }
  },
}
</script>