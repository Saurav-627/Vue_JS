<template>
  <div class="float-end">
    <button class="btn btn-outline-danger" @click="generateLuckyNumber()">
      <span v-if="luckyNumber === 0">
        Generate Lucky Number <br />
        Range(1 - {{ maxNumber }})
      </span>
      <span v-else
        >Lucky Number: {{ luckyNumber }}<br />
        Click to Generate New Lucky Number</span
      >
    </button>
  </div>
</template>
<script setup>
import { ref, inject } from "vue";

let luckyNumber = ref(0);
// const props = defineProps({
//   maxNumber: {
//     type: Number,
//     default: 100,
//   },
// });

const maxNumber = inject("maxLuckyNumber");

//** Generate Lucky Number using props ***/
// function generateLuckyNumber() {
//   luckyNumber.value = Math.floor(Math.random() * props.maxNumber);
//   console.log(luckyNumber.value);
//   return luckyNumber.value;
// }

//** Generate Lucky Number using inject ***/
function generateLuckyNumber() {
  luckyNumber.value = Math.floor(Math.random() * maxNumber.value);
  console.log(luckyNumber.value);
  return luckyNumber.value;
}


</script>
