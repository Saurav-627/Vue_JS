<template>
  <div class="">
    <button class="btn btn-danger text-black" @click="generateLuckyNumber()">
      <span v-if="luckyNumber === 0">
        Generate Lucky Number <br />
        Range(1 - 100)
      </span>
      <span v-else
        >Lucky Number: {{ luckyNumber }}<br />
        Click to Generate New Lucky Number</span
      >
    </button>
  </div>
</template>
<script setup>
//THIS IS TOTALLY NEW FOR BEGINNER CONCEPT GO TO CONTACTOPEDIA COMPONENT

import { ref } from "vue";

let luckyNumber = ref(0);
function generateLuckyNumber() {
  luckyNumber.value = Math.floor(Math.random() * 100);
  console.log(luckyNumber.value);
}
</script>
