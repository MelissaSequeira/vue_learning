<script setup lang="ts">
import {ref} from 'vue'
  const radio=ref<boolean>(false)
</script>
<template>
  <form @submit.prevent>
    <p><input v-model="radio" type="checkbox"></input>Accept the terms and conditions</p>
  </form>
  <p v-if="radio">Continue for more updates!!</p>
  <p v-else>to Continue accept the terms and conditions</p>
</template>
