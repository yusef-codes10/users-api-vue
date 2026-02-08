<script setup>
import { ref, onMounted } from 'vue'

// create users array
const users = ref([
  { firstName: 'Jessica', lastName: 'Anderson', age: 19, gender: 'Female' },
  { firstName: 'Alice', lastName: 'Stones', age: 18, gender: 'Female' },
])

// fetching data from an api
onMounted(() => { async () => {
  const response = await fetch('https://dummyjson.com/users?limit=10')
  const data = await response.json()
}

}),
</script>

<template>
  <div class="user" v-for="user in users" :key="user.firstName">
    <h1>User 1</h1>
    <ul>
      <li>First name: {{ user.firstName }}</li>
      <li>Last name: {{ user.lastName }}</li>
      <li>age: {{ user.age }}</li>
      <li>gender: {{ user.gender }}</li>
    </ul>
  </div>
</template>

<style scoped>
.user {
  display: flex;
  flex-direction: column;
  border: 1px solid #000;
  padding: 1rem 2rem;
  margin: 1rem 0;
}
</style>
