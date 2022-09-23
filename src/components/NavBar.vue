<script setup>
  import { ref } from 'vue'
  import { useAuth } from '@/composables/useAuth'

  const { isAuthenticated } = useAuth()
  const brand = ref('🏢 Fake Company Directory')
</script>

<template>
  <nav>
    <div class="wrapper">
      <RouterLink :to="{ name: 'Home' }" class="brand">
        <span class="brand-title">{{ brand }}</span>
      </RouterLink>
      <div class="menu">
        <RouterLink :to="{ name: 'Home' }" href="#" class="menu-item">Departments</RouterLink>
        <div v-if="isAuthenticated">
          <RouterLink :to="{ name: 'Home' }" href="#" class="menu-item">Settings</RouterLink>
          <RouterLink :to="{ name: 'Home' }" href="#" class="menu-logout">Logout</RouterLink>
        </div>
        <div v-else>
          <RouterLink :to="{ name: 'Login' }" href="#" class="menu-login">Login</RouterLink>
        </div>
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
        div {
          @apply py-2;
        }
        &-item {
          @apply rounded-md px-3 py-2 hover:bg-orange-400 hover:text-slate-200;
        }
        &-login {
          @apply rounded-md bg-blue-500 px-3 py-2 text-slate-100 hover:bg-blue-700;
        }
        &-logout {
          @apply mx-2 rounded-md bg-red-500 px-3 py-2 text-slate-100 hover:bg-red-700;
        }
      }
    }
  }
</style>
