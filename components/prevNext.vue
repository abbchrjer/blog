<template>
  <section id="prev-next" class="flex m-5 gap-12 py-8 items-center justify-between m-auto max-w-xl lg: max-w-4xl">
    <nuxt-link
      v-if="prev"
      :to="{ name: 'posts-slug', params: { slug: prev.slug } }"
      class="prev"
    >
      <span><svg
          xmlns="http://www.w3.org/2000/svg"
          viewBox="-5 -5 24 24"
          width="24"
          height="24"
          preserveAspectRatio="xMinYMin"
          class="icon jam jam-arrow-left"
        >
          <path
            d="M3.414 7.657l3.95 3.95A1 1 0 0 1 5.95 13.02L.293 7.364a.997.997 0 0 1 0-1.414L5.95.293a1 1 0 1 1 1.414 1.414l-3.95 3.95H13a1 1 0 0 1 0 2H3.414z"
          /></svg
      ></span>
      <span> {{ prev.title }} </span>
    </nuxt-link>

    <span class="prev" v-else></span>

    <nuxt-link
      v-if="next"
      :to="{ name: 'posts-slug', params: { slug: next.slug } }"
      class="next"
    >
      <span>{{ next.title }}</span>
      <span>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          viewBox="-5 -5 24 24"
          width="24"
          height="24"
          preserveAspectRatio="xMinYMin"
          class="icon jam jam-arrow-right"
        >
          <path
            d="M10.586 5.657l-3.95-3.95A1 1 0 0 1 8.05.293l5.657 5.657a.997.997 0 0 1 0 1.414L8.05 13.021a1 1 0 1 1-1.414-1.414l3.95-3.95H1a1 1 0 1 1 0-2h9.586z"
          />
        </svg>
      </span>
    </nuxt-link>
    <span class="next" v-else> </span>
  </section>
</template>

<script>
  export default {
    props: {
      prev: {
        type: Object,
        default: () => null,
      },
      next: {
        type: Object,
        default: () => null,
      },
    },
  }
</script>