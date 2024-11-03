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

const titleClass = ref('title')
</script>

<template>
  <h1>{{ message }}</h1>
  <p>Count is {{ counter.count }}</p>
  <h1 v-bind:class="titleClass">Make me dynamic!</h1>
  <h1 :class="titleClass">{{ message.split('').reverse().join('') }}</h1>
</template>

<style>
.title {
  color: red;
}
</style>
