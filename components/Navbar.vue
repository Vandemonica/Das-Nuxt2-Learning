<template>
  <div class="position-fixed w-100" style="z-index: 200;">
    <b-navbar toggleable="lg" class="px-md-5 py-3 bg-dark" type="dark">
      <b-navbar-brand href="/">
        <i>Das Learning</i>
      </b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav class="ml-auto">
          <b-nav-item v-for="(item, key) in navbar" v-bind:key="key" :href="item.url">
            {{ item.label }}
          </b-nav-item>

          <b-nav-form action="/search">
            <div class="w-100 d-flex ml-lg-5">
              <b-form-input size="sm" name="q" class="w-full mr-2" placeholder="Search.."></b-form-input>
              <b-button size="sm" class="bg-primary" type="submit">Search</b-button>
            </div>
          </b-nav-form>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
export default {
  name: 'NuxtNavbar',
  data () {
    return {
      navbar: [
        {
          label: 'Home',
          url: '/'
        },
        {
          label: 'Posts',
          url: '/posts'
        },
        {
          label: 'My Github',
          url: 'https://github.com/vandemonica'
        }
      ]
    }
  }
}
</script>
