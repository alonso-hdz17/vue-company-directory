<script setup>
  import { faker } from '@faker-js/faker'
  const firstName = faker.name.firstName()
  const lastName = faker.name.lastName()
  const fullName = `${firstName} ${lastName}`

  const selectCard = () => {
    console.log(`${fullName} selected`)
  }
</script>

<template>
  <div class="card" @click="selectCard">
    <div class="card-image">
      <img :src="faker.internet.avatar()" alt="" srcset="" />
    </div>
    <div class="card-details">
      <p class="card-details-name">{{ fullName }}</p>
      <p class="card-details-job">{{ faker.name.jobTitle() }}, {{ faker.name.jobArea() }}</p>
      <p class="card-details-email">{{ faker.internet.exampleEmail(firstName, lastName) }}</p>
      <p class="card-details-quote">"{{ faker.lorem.paragraph() }}"</p>
    </div>
  </div>
</template>

<style scoped lang="postcss">
  .card {
    @apply cursor-pointer overflow-hidden rounded-xl bg-slate-200 p-6 shadow-sm transition-transform duration-300 hover:scale-125 hover:shadow-2xl hover:shadow-slate-600;
    &-image {
      img {
        @apply mx-auto rounded-full object-contain;
      }
    }

    &-details {
      @apply flex flex-col gap-1 pt-6 text-center;
      &-name {
        @apply text-2xl font-bold tracking-wide text-black;
      }
      &-job {
        @apply text-lg font-semibold text-slate-700;
      }
      &-email {
        @apply text-sm font-semibold text-orange-300;
      }
      &-quote {
        @apply pt-2 text-sm font-semibold italic;
      }
    }
  }
</style>
