<template>
  <div>
    <h1 class="display-6">All Posts</h1>
    <div class="row">
      <NuxtLink v-for="(item, key) in posts" v-bind:key="key" :to="`/posts/${item.id}`" class="col-12 col-lg-6 text-decoration-none">
        <PostCard :item="item" />
      </NuxtLink>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PostsIndexPage',
  layout: 'BasicLayout',
  data () {
    return {
      posts: []
    }
  },
  async fetch () {
    this.posts = await this.$axios.$get('https://jsonplaceholder.typicode.com/posts')
  }
}
</script>
