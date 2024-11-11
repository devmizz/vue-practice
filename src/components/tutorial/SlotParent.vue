<script setup>
import SlotChild from "@/components/tutorial/SlotChild.vue";
import {ref} from "vue";

const unslotProps = ref("slot 안 넘겨")
const slotProps = ref("slot 넘겨")
</script>

<template>
  <div>
    <SlotChild :msg="slotProps">
      안녕하세요 Slot 입니다.
    </SlotChild>
  </div>

  <div>
    <SlotChild :msg="unslotProps"/>
  </div>

</template>
