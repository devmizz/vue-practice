<script setup>
import {ref, watch} from 'vue'
import Child from "@/components/Child.vue";

const todoId = ref(1)
const todoData = ref(null)
const propsMessage = ref("props message")
const childMessage = ref("Not yet")

async function fetchData() {
  todoData.value = null
  const res = await fetch(
    `https://jsonplaceholder.typicode.com/todos/${todoId.value}`
  )
  todoData.value = await res.json()
}

// 최초 1회 fetch
fetchData()

// watch(todoId, (newTodoId) => {
//   todoData.value.id = newTodoId
//   fetchData()
// })

watch(todoId, fetchData)
</script>

<template>
  <p>Todo id: {{ todoId }}</p>
  <button @click="todoId++" :disabled="!todoData">Fetch next todo</button>
  <p v-if="!todoData">Loading...</p>
  <pre v-else>{{ todoData }}</pre>

  <div>
    <Child :msg="propsMessage"/>
    <Child @response="(childMsg) => childMessage = childMsg"/>
    <p>child message: {{ childMessage }}</p>
  </div>
</template>
