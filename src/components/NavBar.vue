<script setup>
  import { ref } from 'vue'
  const brand = ref('🏢 Fake Company Directory')
</script>

<template>
  <nav>
    <div class="wrapper">
      <RouterLink :to="{ name: 'Home' }" class="brand">
        <span class="brand-title">{{ brand }}</span>
      </RouterLink>
      <div class="menu">
        <a href="#" class="menu-item">Departments</a>
        <a href="#" class="menu-item">Settings</a>
        <a href="#" class="menu-login">Logout</a>
      </div>
    </div>
  </nav>
</template>

<style scoped lang="postcss">
  nav {
    @apply flex h-20 bg-black text-slate-50;
    .wrapper {
      @apply container mx-auto flex w-full items-center justify-between;
      .brand {
        &-title {
          @apply text-2xl font-bold text-slate-300;
        }
      }
      .menu {
        @apply flex gap-2;
        &-item {
          @apply rounded-md px-3 py-2 hover:bg-orange-400 hover:text-slate-200;
        }
        &-login {
          @apply rounded-md bg-red-500 px-3 py-2 text-slate-100 hover:bg-red-700;
        }
      }
    }
  }
</style>
