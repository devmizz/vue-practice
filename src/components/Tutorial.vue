<script setup>
import {reactive, ref} from 'vue'

const counter = reactive({
  count: 0
})

console.log(counter.count)
counter.count++

const message = ref('Hello World!')
console.log(message.value)
message.value = 'Changed'
</script>

<template>
  <h1>{{ message }}</h1>
  <p>Count is {{ counter.count }}</p>
  <h1>Make me dynamic!</h1>
  <h1>{{ message.split('').reverse().join('') }}</h1>
</template>
