<script setup>
  import MainSearch from '@/components/MainSearch.vue'
  import MainCards from '@/components/MainCards.vue'
  import MainPagination from '@/components/MainPagination.vue'
</script>

<template>
  <div class="wrapper">
    <MainSearch />
    <MainCards />
    <MainPagination />
  </div>
</template>

<style scoped lang="postcss">
  .wrapper {
    @apply container mx-auto flex w-11/12 flex-col gap-4 py-3;
  }
</style>
