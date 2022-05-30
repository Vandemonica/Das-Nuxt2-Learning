<template>
  <div v-if="$fetchState.pending">
    <div class="mt-5 pt-5 text-center">
      <img src="/loading.gif" alt="loading..">
      <h3>Now Loading..</h3>
    </div>
  </div>
  <div v-else-if="!$fetchState.error" style="max-width: 800px">
    <h2>{{ post.title }}</h2>
    <div class="d-flex text-muted">
      <div class="mr-4">By: user-{{ post.userId }}</div>
      <div>Post Id: {{ this.$route.params.id }}</div>
    </div>
    <div>
      {{ post.body }}
    </div>
  </div>
  <div v-else>
    <div class="mt-5 pt-5 text-center">
      <h1 class="text-danger">Oopsy :(</h1>
      <h3>It seems we can't get the post</h3>

      <div class="d-flex justify-content-center mt-2">
        <button @click="$fetch" class="btn btn-outline-primary mr-2">Try Again</button>
        <NuxtLink to="/posts" class="btn btn-primary">Take Me Back</NuxtLink>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PostsPage',
  layout: 'BasicLayout',
  data () {
    return {
      post: []
    }
  },
  async fetch () {
    this.post = await this.$axios.$get(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
  }
}
</script>
