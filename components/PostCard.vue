<template>
  <div class="card mb-3" style="height: 260px">
    <div class="card-body d-flex flex-column">
      <h3 class="mb-0">{{ item.title }}</h3>
      <div class="text-muted">By: user-{{ item.userId }}</div>

      <div class="mt-auto text-dark">
        {{ item.body }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NuxtPostCard',
  props: {
    item: []
  }
}
</script>
