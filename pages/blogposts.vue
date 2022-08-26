<template>
<div>
  <div class="grid grid-cols-1 lg:grid-cols-2 lg:gap-x-4 place-content-center max-w-screen-lg m-auto px-4 lg:px-0 font-display mt-12 mb-12">
    <div class="">
        <h2 class="text-5xl md:text-5xl text-grey-990 leading-snug tracking-tighter mb-3 font-medium">
            Recent articles
        </h2>
        The latest thoughts, experiments, and essays.
    </div>

           <div class="flex justify-bottom relative p-2 mx-auto text-gray-600">
        <input v-model="searchQuery" class="border-2 border-gray-300 bg-white h-10 px-5 pr-16 rounded-lg text-sm focus:outline-none"
          type="search" name="search" placeholder="Search articles">
        <button type="submit" class="absolute right-0 top-0 mt-5 mr-4" @click="toggle($event)">
          <svg class="text-gray-600 h-4 w-4 fill-current" xmlns="http://www.w3.org/2000/svg"
            xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" id="Capa_1" x="0px" y="0px"
            viewBox="0 0 56.966 56.966" style="enable-background:new 0 0 56.966 56.966;" xml:space="preserve"
            width="512px" height="512px">
            <path
              d="M55.146,51.887L41.588,37.786c3.486-4.144,5.396-9.358,5.396-14.786c0-12.682-10.318-23-23-23s-23,10.318-23,23  s10.318,23,23,23c4.761,0,9.298-1.436,13.177-4.162l13.661,14.208c0.571,0.593,1.339,0.92,2.162,0.92  c0.779,0,1.518-0.297,2.079-0.837C56.255,54.982,56.293,53.08,55.146,51.887z M23.984,6c9.374,0,17,7.626,17,17s-7.626,17-17,17  s-17-7.626-17-17S14.61,6,23.984,6z" />
          </svg>
        </button>
      </div>

    <div class="flex space-x-2 space-y-2 flex-wrap lg:justify-end lg:mt-0 mt-5 flex text-xs items-end">

      <div class="bg-blue-300 hover:bg-blue-400 transition duration-200 py-2 px-3 shadow-sm rounded-sm cursor-pointer" @click="toggle($event)">
          Chicken
      </div>
      <div class="bg-red-300 hover:bg-red-400 transition duration-200 py-2 px-3 shadow-sm rounded-sm cursor-pointer" @click="toggle($event)">
          Seafood
      </div>
      <div class="bg-yellow-200 hover:bg-yellow-300 transition duration-200 py-2 px-3 shadow-sm rounded-sm cursor-pointer" @click="toggle($event)">
          Pasta
      </div>
      <div class="bg-teal-200 hover:bg-teal-300 transition duration-200 py-2 px-3 shadow-sm rounded-sm cursor-pointer" @click="toggle($event)">
          Salad
      </div>
      <div class="bg-cyan-300 hover:bg-cyan-400 transition duration-200 py-2 px-3 shadow-sm rounded-sm cursor-pointer" @click="toggle($event)">
          Soup
      </div>
      <div class="bg-fuchsia-300 hover:bg-fuchsia-400 transition duration-200 py-2 px-3 shadow-sm rounded-sm cursor-pointer" @click="toggle($event)">
          Spicy
      </div>


    </div>
  </div>

    <ul class="grid flex md:grid-cols-2 md:gap-4 xs:grid-cols-1 lg:grid-cols-3 lg:gap-8 m-8" v-if="this.selected.length > 0" :key="compKey">
      <PostPreview v-for="post in filtered" :key="post.slug" :post="post"></PostPreview>
    </ul>
    <div v-else class="max-w-screen-lg mx-auto px-4 lg:px-0 mb-12">There are no posts left. Have you tried adding a category?<div class="flex h-screen"></div></div>


    <!-- <div class="flex flex-col items-center mb-8 px-4 mx-auto mt-8">
        <div class="font-sans flex justify-end space-x-1 select-none">
            <a href="" class="flex items-center px-4 py-2 text-gray-500 bg-gray-300 rounded-md" style="transition: all 0.2s ease;">
                Previous
            </a>
            <a href="/blogposts" class="px-4 py-2 text-gray-700 bg-gray-200 rounded-md hover:bg-sky-500 hover:text-white" style="transition: all 0.2s ease;">
                1
            </a>
            <a href="/blogposts2" class="px-4 py-2 text-gray-700 bg-gray-200 rounded-md hover:bg-sky-500 hover:text-white" style="transition: all 0.2s ease;">
                2
            </a>
            <a href="/blogposts3" class="px-4 py-2 text-gray-700 bg-gray-200 rounded-md hover:bg-sky-500 hover:text-white" style="transition: all 0.2s ease;">
                3
            </a>
            <span class="px-4 py-2 text-gray-700  rounded-md" >
                ...
            </span>
            <a href="#" class="px-4 py-2 text-gray-700 bg-gray-200 rounded-md hover:bg-sky-500 hover:text-white" style="transition: all 0.2s ease;">
                7
            </a>
            <a href="#" class="px-4 py-2 font-bold text-gray-500 bg-gray-300 rounded-md hover:bg-sky-500 hover:text-white" style="transition: all 0.2s ease;">
                Next
            </a>
        </div>
    </div> -->
<!-- </div> -->



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

  data() {
      return {
        searchQuery: null,
          selected: ["Chicken", "Seafood", "Pasta", "Salad", "Soup", "Spicy"],
          compKey: 0,
      };
  },

  methods: {
      toggle(event){
          this.compKey++;
          const element = event.target;
          const text = element.textContent.trim();

          if (this.selected.includes(text)){
              element.classList.add("opacity-50");
              this.selected.splice(this.selected.indexOf(text), 1);
          } else {
              element.classList.remove("opacity-50");
              this.selected.push(text);
          }
          console.log(this.selected)
      },
  },

  computed: {
      filtered() {
          if (this.selected.length == 0) {
              return;
          } else {
            //  return this.posts.filter(post => this.selected.includes(post.tags))

             let array = this.posts;
             let newArr = [];

             for (let i = 0; i < array.length; i++){
               let hasElem = false;
              // let hasAllElems = true;
              //  for (let j = 0; j < (array[i].tags).length; j++){
              //  if ((this.selected).indexOf(array[i].tags[j]) === -1) {
              //    hasAllElems = false;
              //    }
              //  }
              //  if (hasAllElems == true) newArr.push(array[i]);


              for(let j = 0; j < (array[i].tags).length; j++) {

        for(let k = 0; k < (this.selected).length; k++) {

            if((array[i].tags)[j] == (this.selected)[k]) {

                hasElem = true;
            }
        }
    } if (hasElem == true) newArr.push(array[i]);



             }
      if (this.searchQuery) {
        return this.posts.filter(item => {
          return this.searchQuery
            .toLowerCase()
            .split(" ")
            .every(v => item.title.toLowerCase().includes(v));
        });
      } else {
        return newArr;
      }
          }
      }
  },
}
</script>
