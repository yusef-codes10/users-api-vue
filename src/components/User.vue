<script setup>
import { ref } from 'vue'

const firstName = ref('Jessica')
const lastName = ref('Anderson')
const age = ref(19)
const gender = ref('Female')
</script>

<template>
  <div class="user">
    <h1>User 1</h1>
    <ul>
      <li>First name: {{ firstName }}</li>
      <li>Last name: {{ lastName }}</li>
      <li>age: {{ age }}</li>
      <li>gender: {{ gender }}</li>
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
