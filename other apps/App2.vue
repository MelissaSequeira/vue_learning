
<script setup lang="ts">
import { ref } from 'vue'
  const name=ref<string>("");
  const show=ref<string>("");
  const onClick=():void=>{
    show.value=name.value;
  }

</script>

<template>
  <div>
    <h3 v-if="show">Hello {{show}}</h3>
    <h3 v-else>Enter the name</h3>
  </div>
 <form @submit.prevent>
 <p>Name:<input v-model="name" placeholder="enter name"></p>
 <button @click="onClick"  type="submit">Submit</button>
 </form>
</template>
