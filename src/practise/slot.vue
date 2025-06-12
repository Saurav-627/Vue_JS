<!-- With the use of slot we can pass data from parent to child components. -->

<!-- PASSING FROM PARENT COMPONENT  -->
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

<!-- Without using slot the p tag content from up will not render in child component but
  if we use slot the p tag content will render in child component. -->

<!-- The slot data always belongs to parent component -->

<!-- We can give name to the slot by using template and inside template v-slot:name which is used above -->

<!-- USING SLOT  -->
<template>
  <div class="bg-dark text pt-3" :style="{ height: '100vh' }">
    <h1 class="text-center text-success">Learn Slot</h1>
    <div class="container text-center bg-white">
      <slot></slot>
      <slot name="learnSlot"></slot>
      <slot name="moreInfo"></slot>
      <button
        class="btn btn-primary text-black m-2"
        @click="newVersion = !newVersion"
      >
        Toggle Component</button
      ><br />
      <button
        class="btn btn-primary text-black m-2"
        @click="newVersion = false"
      >
        Lucky Number V1
      </button>
      <button class="btn btn-primary text-black m-2" @click="newVersion = true">
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
