<template>
  <div>
    <Tutorial />
    <NuxtLink to="/about">
      About (internal link that belongs to the Nuxt App)
    </NuxtLink>
    <div>{{ ip }}</div>
    <ul>
      <li v-for="(post, index) in postsList" :key="index">{{ post.title }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  async asyncData ({ $axios }) {
    const ip = await $axios.$get('http://icanhazip.com')
    const postsList = await $axios.$get('https://jsonplaceholder.typicode.com/posts')
    return { ip, postsList }
  }
}
</script>
