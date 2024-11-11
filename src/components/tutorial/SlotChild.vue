<script setup>
const props = defineProps({
  msg: String
})
</script>

<template>
  <div>
    <h1>{{ msg }} / slot fallback을 지정해놓은 경우</h1>
    <slot>
      Slot Fallback
    </slot>
  </div>

  <div>
    <h1>{{ msg }} / slot fallback을 지정하지 않은 경우</h1>
    <slot/>
  </div>
</template>
