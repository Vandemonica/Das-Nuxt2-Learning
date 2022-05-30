<template>
  <div>
    <Navbar />

    <div class="container min-vh-100 py-5">
      <div class="py-5">
        <Nuxt />
      </div>
    </div>

    <Footer />
  </div>
</template>

<script>
export default {
  name: 'BasicLayout'
}
</script>
