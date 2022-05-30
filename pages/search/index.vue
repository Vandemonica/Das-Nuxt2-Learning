<template>
  <div>
    <div class="card mt-3 mb-5 bg-light mx-auto" style="max-width: 600px">
      <div class="card-body">
        <h4>Search some posts by title</h4>
        <form class="d-flex" method="GET">
          <input type="text" name="q" class="form-control mr-2" :value="this.$route.query.q ? this.$route.query.q : ''" placeholder="Search..">
          <button class="btn btn-primary">Search</button>
        </form>
      </div>
    </div>

    <div v-if="$fetchState.pending">
      <div class="mt-5 pt-5 text-center">
        <img src="/loading.gif" alt="loading..">
        <h3>Now Loading..</h3>
      </div>
    </div>
    <div v-else-if="this.$route.query.q && posts.length != 0">
      <h4>Search result of: "{{ this.$route.query.q }}"</h4>
      <div class="row">
        <NuxtLink v-for="(item, key) in posts" v-bind:key="key" :to="`/posts/${item.id}`" class="col-12 col-lg-6 text-decoration-none">
          <PostCard :item="item" />
        </NuxtLink>
      </div>
    </div>
    <div v-else-if="this.$route.query.q && posts.length == 0">
      <div class="mt-5 pt-5 text-center">
        <h1 class="text-danger">No matching posts found</h1>
        <h3>No result for "{{ this.$route.query.q }}", try searching something else</h3>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SearchIndexPage',
  layout: 'BasicLayout',
  data () {
    return {
      posts: []
    }
  },
  async fetch () {
    const posts = await this.$axios.$get('https://jsonplaceholder.typicode.com/posts')
    const search = this.$route.query.q

    this.posts = posts.filter(x => x.title.toLowerCase().includes(search.toLowerCase()))
  }
}
</script>
