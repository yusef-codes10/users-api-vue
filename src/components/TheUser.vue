<script setup>
import { ref, onMounted, computed } from 'vue'

// create users array
// const users = ref([
//   { firstName: 'Jessica', lastName: 'Anderson', age: 19, gender: 'Female' },
//   { firstName: 'Alice', lastName: 'Stones', age: 18, gender: 'Female' },
// ])
const users = ref([])

// fetching data from an api
onMounted(async () => {
  try {
    // getting data from api & turning it into json
    const response = await fetch('https://dummyjson.com/users?limit=20')
    const data = await response.json()

    // mapping/transforming the array
    users.value = data.users.map((user) => ({
      id: user.id,
      firstName: user.firstName,
      lastName: user.lastName,
      age: user.age,
      gender: user.gender,
      bloodGroup: user.bloodGroup,
    }))
  } catch (err) {
    console.error(err)
  }
})

// trying to filter the famles only here
// Computed props are derived variables not functions, to create filters we fdo this:
// 1️⃣ create the states
const showFemales = ref(false)
const showOMinusBlood = ref(false)

const filterdUsers = computed(() => {
  let result = users.value

  if (showFemales.value) {
    result = result.filter((user) => user.gender === 'female')
  }

  if (showOMinusBlood.value) {
    result = result.filter((user) => user.bloodGroup === 'O-')
  }

  return result
})

// we need the show females only function
const showFemalesOnly = () => {
  showFemales.value = !showFemales.value
}

const showOBlood = () => {
  showOMinusBlood.value = !showOMinusBlood.value
}

// adding the o- blood filter
</script>

<template>
  <button @click="showFemalesOnly">Get Females only</button>
  <button @click="showOBlood">O-</button>
  <div class="user" v-for="user in filterdUsers" :key="user.id">
    <h1>User {{ user.id }}</h1>
    <ul>
      <li>First name: {{ user.firstName }}</li>
      <li>Last name: {{ user.lastName }}</li>
      <li>age: {{ user.age }}</li>
      <li>gender: {{ user.gender }}</li>
      <li>Blood Group: {{ user.bloodGroup }}</li>
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
