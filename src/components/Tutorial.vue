<script setup>
import {reactive, ref} from 'vue'

const counter = reactive({
  count: 0
})
const message = ref('Hello World!')
const titleClass = ref('title')
const text = ref('')
const textClass = ref('text')
const isAwesome = ref(true)

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

function toggle() {
  isAwesome.value = !isAwesome.value
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
    <p :class="textClass">{{ text }}</p>
  </div>
  <div>
    <button @click="toggle">Toggle</button>
    <h1 v-if="isAwesome">Vue is awesome!</h1>
    <h1 v-else>Oh no</h1>
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
