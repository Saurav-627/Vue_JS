<template>
  <div class="container">
    <div>{{ message }}</div>
    Contact owner name: <input type="text" v-model="ownerName" />
    <div class="row">
      <div class="col-12" v-for="contact in contacts" :key="contact.name">
        <Contact
          :name="contact.name"
          :phone="contact.phone"
          :email="contact.email"
          :ownerName="contact.ownerName"
          :isFavorite="contact.isFavorite"
          @update-favorite="contact.isFavorite = !contact.isFavorite"  
        ></Contact>
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive, ref } from "vue";
import Contact from "./components/Contact.vue";
const message = "Hello Vue";
const ownerName = ref("masteryVue");

const contacts = reactive([
  {
    name: "Saurav Luitel",
    phone: 9800000000,
    email: "saurav@gmail.com",
    ownerName: ownerName,
    isFavorite: true,
  },
  {
    name: "Sourabh Luitel",
    phone: 9800000000,
    email: "sourabh@gmail.com",
    ownerName: ownerName,
    isFavorite: false,
  },
  {
    name: "Ganguli Luitel",
    phone: 9800000000,
    email: "ganguli@gmail.com",
    ownerName: ownerName,
    isFavorite: false,
  },
]);
</script>

<style></style>
