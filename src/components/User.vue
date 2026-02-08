<script setup>
import { ref } from 'vue'

const firstName = ref('Jessica')
const lastName = ref('Anderson')
const age = ref(19)
const gender = ref('Female')
</script>

<template>
  <h1>User 1</h1>
  <ul>
    <li>First name:</li>
    <li>Last name:</li>
    <li>age:</li>
    <li>gender:</li>
  </ul>
</template>

<style scoped></style>
