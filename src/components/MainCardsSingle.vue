<script setup>
  import { ref } from 'vue'
  import { faker } from '@faker-js/faker'

  import useAPI from '@/composables/useAPI'
  const { getDepartment } = useAPI()

  const selectCard = () => {
    console.log(`${props.employee.name} selected`)
  }

  const props = defineProps({
    employee: {
    type: Object,
    required: true,
    default: () => {
      return {
        createdAt: '2022-01-01',
        departmentId: '123',
        email: 'john.doe@example.com',
        employeeId: '123',
        name: 'John Doe',
        quote: 'Really Cool Quote',
        title: 'Position',
        updatedAt: '2022-01-01',
        }
      },
    },
  })
  
  const departmentResponse = await getDepartment(props.employee.departmentId)
  const department = ref(departmentResponse)
</script>

<template>
  <div class="card" @click="selectCard">
    <div class="card-image">
      <img :src="faker.internet.avatar()" alt="" srcset="" />
    </div>
    <div class="card-details">
      <p class="card-details-name">{{ props.employee.name }}</p>
      <p class="card-details-job">{{ props.employee.title }}, {{ department.name }}</p>
      <p class="card-details-quote">"{{ props.employee.quote }}"</p>
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
      &-quote {
        @apply pt-2 text-sm font-semibold italic;
      }
    }
  }
</style>
