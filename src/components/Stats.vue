

<script setup lang="ts">

defineProps<{
  total: number
  applied:number
  accepted:number
  rejected:number
}>()

</script>
<template>
    <div>
        <h5>Application statistics</h5>
        <p>Total jobs applied : {{ total }}</p>
        <p>Jobs applied : {{ applied }}</p>
        <p>Applications accepted : {{ accepted }}</p>
        <p>Applications rejected : {{ rejected }}</p>
    </div>
</template>
<style lang="scss" scoped>

</style>