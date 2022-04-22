<template>
<div>
  <nav class="sticky z-50 top-0 relative flex flex-wrap items-center justify-between px-2 py-2 bg-gradient-to-r from-sky-500 to-indigo-500">
    <div class="container px-4 mx-auto flex flex-wrap items-center justify-between">
      <div div class="w-full relative flex justify-between lg:w-auto  px-4 lg:static lg:block lg:justify-start">
        <a class="text-xl font-bold leading-relaxed inline-block mr-4 py-2 whitespace-nowrap uppercase text-white" href="/home">
          Justini Innovation
        </a>
        <!-- <button class="text-white bg-yellow-300 cursor-pointer text-xl leading-none px-3 py-1 border border-solid border-transparent rounded bg-transparent block lg:hidden outline-none focus:outline-none" type="button" v-on:click="toggleNavbar()">
          <font-awesome-icon :icon="['fas', 'bars']"/> -->

        <!-- <div>
      <button class="relative group block lg:hidden outline-none focus:outline-none" type="button" v-on:click="toggleNavbar()">
        <div class="relative flex overflow-hidden items-center justify-center rounded-full w-[50px] h-[50px] transform transition-all">
          <div class="flex flex-col justify-between w-[20px] h-[20px] transform transition-all duration-300 origin-center overflow-hidden">
            <div class="bg-white h-[2px] w-7 transform transition-all duration-300 origin-left group-focus:translate-x-10"></div>
            <div class="bg-white h-[2px] w-7 rounded transform transition-all duration-300 group-focus:translate-x-10 delay-75"></div>
            <div class="bg-white h-[2px] w-7 transform transition-all duration-300 origin-left group-focus:translate-x-10 delay-150"></div>

            <div class="absolute items-center justify-between transform transition-all duration-500 top-2.5 -translate-x-10 group-focus:translate-x-0 flex w-0 group-focus:w-12">
              <div class="absolute bg-white h-[2px] w-5 transform transition-all duration-500 rotate-0 delay-300 group-focus:rotate-45"></div>
              <div class="absolute bg-white h-[2px] w-5 transform transition-all duration-500 -rotate-0 delay-300 group-focus:-rotate-45"></div>
            </div>
          </div>
        </div>
      </button>
    </div> -->

    <div class=" flex flex-col justify-center lg:hidden" type="button" v-on:click="toggleNavbar()">
    <div class="relative sm:max-w-xl mx-auto">
        <nav>
            <button class="text-white w-10 h-10 relative focus:outline-none" @click="open = !open">
                <div class="block w-5 absolute left-1/2 top-1/2   transform  -translate-x-1/2 -translate-y-1/2">
                    <span aria-hidden="true" class="block absolute h-0.5 w-5 bg-current transform transition duration-500 ease-in-out" :class="{'rotate-45': open,' -translate-y-1.5': !open }"></span>
                    <span aria-hidden="true" class="block absolute  h-0.5 w-5 bg-current   transform transition duration-500 ease-in-out" :class="{'opacity-0': open } "></span>
                    <span aria-hidden="true" class="block absolute  h-0.5 w-5 bg-current transform  transition duration-500 ease-in-out" :class="{'-rotate-45': open, ' translate-y-1.5': !open}"></span>
                </div>
            </button>
        </nav>
    </div>
</div>


<div class="hidden lg:block">
      <div class="lg:flex lg:flex-grow items-center">

        <ul class="flex flex-col lg:flex-row justify-center list-none ml-auto">
          <li class="nav-item transition-colors duration-300">
            <a class="px-3 py-2 flex items-center text-base uppercase font-bold leading-snug text-white hover:opacity-75" href="/home">
              <i class=" text-sm leading-lg text-white opacity-75" /><span class="ml-2">Home</span>
            </a>
            </li>
            <li class="nav-item transition-colors duration-300">
            <a class="px-3 py-2 flex items-center text-base uppercase font-bold leading-snug text-white hover:opacity-75" href="/blogposts">
              <i class=" text-sm leading-lg text-white opacity-75" /><span class="ml-2">Posts</span>
            </a>
          </li>
          <li class="nav-item transition-colors duration-300">
            <a class="px-3 py-2 flex items-center text-base uppercase font-bold leading-snug text-white hover:opacity-75" href="/about">
              <i class=" text-sm leading-lg text-white opacity-75" /><span class="ml-2">About</span> 
            </a>
          </li>
        </ul>
      </div>
      </div>





</div>
</div>
  </nav>

<div class=" absolute z-49">
          <transition
        enter-active-class="transform transition duration-500 ease-custom"
        enter-class="-translate-y-1/2 scale-y-0 opacity-0"
        enter-to-class="translate-y-0 scale-y-100 opacity-100"
        leave-active-class="transform transition duration-300 ease-custom"
        leave-class="translate-y-0 scale-y-100 opacity-100"
        leave-to-class="-translate-y-1/2 scale-y-0 opacity-0"
      >
        <ul
          v-show="showMenu"
          class="left-0 right-0 divide-y shadow-lg overflow-hidden flex flex-col lg:flex-row list-none ml-auto bg-gradient-to-r from-sky-500 to-indigo-500"
        >
          <li
            v-for="(option, index) in options"
            :key="index"
            class="px-3 py-1 transition-colors duration-300 flex justify-start w-screen"
          ><a v-if="hrefs[index]"
          :href="hrefs[index]"
          class="px-3 py-2 flex items-center text-base uppercase font-bold leading-snug text-white hover:opacity-75">
            <i class=" text-sm leading-lg opacity-75" /><span class="ml-2">{{ option }}</span></a>
          </li>
        </ul>
      </transition>
      </div>
      </div>
</template>

<script>
export default {
  name: "navbar",
  data() {
    return {
      showMenu: false,
      open: false,

      options: ["Home", "Posts", "About"],
      hrefs: ["/home", "/blogposts", "/about"],
    }
  },
  methods: {
    toggleNavbar: function(){
      this.showMenu = !this.showMenu;
    },

  }
}
</script>


<style>
.ease-custom {
  transition-timing-function: cubic-bezier(.61,-0.53,.43,1.43);
}
</style>