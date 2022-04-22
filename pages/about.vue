<template>
<article>
  <!-- <article class="grid grid-cols-12 pb-24 mt-8">
    <div class="flex w-full col-start-2 col-span-5">
      <div class="w-full">
          <NuxtLink to="/home" href="/home" class="block text-gray-400 mt-8">← Go Back</NuxtLink>
          <h1 class="text-5xl font-black mt-2">{{ post.title }}</h1>
        <nuxt-content class=" mt-4 prose max-w-none" :document="post" />
      </div>
    </div> -->



<!-- 
    <div class="flex col-start-8 col-span-3 justify-center">
        <nuxt-img
        class="flex max-w-full h-auto"
        :src= "post.img1"
        width="768"
        height="509"
        />
        <nuxt-img
        class="flex max-w-full h-auto"
        :src= "post.img2"
        width="768"
        height="509"
        />
</div> -->


<!-- <div class="container mx-auto">
    <div class="grid grid-cols-1 md:grid-cols-2 h-screen">
      <div class="max-h-96 md:h-screen">
        <img class="w-screen h-screen object-cover object-top" src="https://images.pexels.com/photos/270373/pexels-photo-270373.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=650&w=940" alt="">
      </div>
      <div class="flex p-10">
        <div class="mb-auto mt-auto max-w-lg">
          <h1 class="text-3xl uppercase">Christopher Jernberg</h1>
          <p class="font-semibold mb-5">Professional Css Master</p>
          <p>Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Donec odio. Quisque volutpat mattis eros. Nullam malesuada erat ut turpis. Suspendisse urna nibh, viverra non, semper suscipit, posuere a, pede.</p>
          <button class="bg-black rounded-md py-3 px-7 mt-6 text-white">Email Me</button>
        </div>
      </div>
    </div>
  </div> -->



<div class="py-16 bg-white">  
  <div class="container m-auto md:px-12 xl:px-6">
      <div class="space-y-6 md:space-y-0 md:flex md:gap-6 lg:items-center lg:gap-12">
                        <div class="md:5/12 lg:w-5/12 m-5">
          <nuxt-img :src="post.img" alt="image" loading="lazy" width="" height=""/>
        </div>
        <div class="md:7/12 lg:w-6/12 m-5">
          <NuxtLink to="/home" href="/home" class="block text-gray-400 mt-8">← To Home</NuxtLink>
          <h1 class="text-5xl font-black mt-2">{{ post.title }}</h1>
        <nuxt-content class=" mt-4 prose max-w-none" :document="post" />
        </div>
      </div>
  </div>
</div>

<div class="flex h-screen"></div>

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