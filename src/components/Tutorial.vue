<script setup>
import {reactive, ref} from 'vue'

const counter = reactive({
  count: 0
})
const message = ref('Hello World!')
const titleClass = ref('title')
const text = ref('')
const textClass = ref('text')

console.log(counter.count)
counter.count++

console.log(message.value)
message.value = 'Changed'

function increment() {
  counter.count++
}

function onInput(e) {
  text.value = e.target.value
}
</script>

<template>
  <h1>{{ message }}</h1>
  <p>Count is {{ counter.count }}</p>
  <h1 v-bind:class="titleClass">Make me dynamic!</h1>
  <h1 :class="titleClass">{{ message.split('').reverse().join('') }}</h1>
  <div>
    <button v-on:click="increment">Count is {{ counter.count }}</button>
    <button @click="increment">Count is {{ counter.count }}</button>
  </div>
  <div>
    <input :value="text" @input="onInput" placeholder="Type here">
    <input :value="text" v-on:input="onInput" placeholder="Type here">
    <p :class="textClass">{{text}}</p>
  </div>
</template>

<style>
.title {
  color: red;
}
.text {
  color: white;
}
</style>
