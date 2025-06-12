<template>
  <LuckyNumberParentComponent>
    <p class="pt-2">We have two version for picking lucky number.</p>
    <template v-slot:moreInfo>
      <p>Click the button to to toggle between the two version</p>
    </template>
    <template v-slot:learnSlot>
      <button @click="showMessage">What will we learn?</button>
      <h4 class="text-success">{{ message }}</h4>
    </template>
    <hr />
  </LuckyNumberParentComponent>
</template>
<script setup>
import { ref } from "vue";
import LuckyNumberParentComponent from "./components/LuckyNumberParentComponent.vue";

const message = ref("");
const showMessage = () => {
  message.value = "We will learn how to use slot";
};
</script>
