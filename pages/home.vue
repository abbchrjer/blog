<template>
<div>

 <div class= "w-full h-96 bg-no-repeat bg-cover bg-fixed" style="background-image: url(/images/food.jpg)">
  </div>

  <div>
    <h1 class="text-6xl font-black m-12">Latest posts</h1>
    <ul class="grid flex md:grid-cols-2 md:gap-4 xs:grid-cols-1 lg:grid-cols-3 lg:gap-8 m-8">
      <PostPreview v-for="post in computedObj" :key="post.slug" :post="post"></PostPreview>
    </ul>
  </div>

  <div class=" flex space-x-3 space-y-3 flex-wrap justify-center text-lg items-end mt-5 font-bold mb-12 mt-12">
        <div class="flex bg-sky-500 hover:bg-sky-600 transition duration-200 py-5 px-12 shadow-sm rounded-lg cursor-pointer text-white text-bold">View more posts
        </div>
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
      limit: 5
    }
  },
  computed:{
  computedObj(){
    return this.limit ? this.posts.slice(0,this.limit) : this.posts
  }
},
}
</script>
