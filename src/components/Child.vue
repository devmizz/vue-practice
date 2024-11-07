<script setup>
const props = defineProps({
  msg: String
})
</script>

<template>
  <h1>I'm Child Component</h1>
  <h2>{{ msg || 'No props passed yet' }}</h2>
</template>
