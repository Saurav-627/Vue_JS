<template>
  <div class="bg-dark text pt-3" :style="{ height: '100vh' }">
    <h1 class="text-center text-success">Learn Slot</h1>
    <div class="container text-center bg-white">
      <slot></slot>
      <slot name="learnSlot"></slot>
      <slot name="moreInfo"></slot>
      <button
        class="btn btn-primary text-white m-2"
        @click="newVersion = !newVersion"
      >
        Toggle Component</button
      ><br />
      <button
        class="btn btn-primary text-white m-2"
        @click="newVersion = false"
      >
        Lucky Number V1
      </button>
      <button class="btn btn-primary text-white m-2" @click="newVersion = true">
        Lucky Number V2
      </button>

      <!-- <LuckyNumber></LuckyNumber>
        <br />
        <LuckyNumberV2></LuckyNumberV2> -->

      <!-- Conditonal rendering component -->
      <!-- <component :is="currentComponent"></component> -->

      <!-- When i toggle the component the input ref from V2 is reseting so to keep it alive we use: -->
      <!-- <keep-alive>
          <component :is="currentComponent"></component>
        </keep-alive> -->
      <!-- To include only 1 component not other then: -->
      <!-- For multiple component use array include="['l','lv2']"  to exclude the component use exclude="['l','lv2']" -->

      <keep-alive include="LuckyNumberV2">
        <component :is="currentComponent" class="border"></component>
      </keep-alive>
    </div>
  </div>
</template>

<script setup>
import { computed, ref } from "vue";
import LuckyNumber from "./LuckyNumber.vue";
import LuckyNumberV2 from "./LuckyNumberV2.vue";

const newVersion = ref(true);

const currentComponent = computed(() => {
  return newVersion.value ? LuckyNumberV2 : LuckyNumber;
});
</script>

<style></style>
