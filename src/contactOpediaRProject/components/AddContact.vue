<template>
  <div class="container border rounded-2">
    <div class="text-center text-white">Add New Contact</div>
    <form @submit.prevent="addContact">
      <div class="row">
        <div class="col-4">
          <input
            type="text"
            class="form-control"
            id="name"
            v-model="contact.name"
            placeholder="Enter Name"
            autocomplete="off"
          />
        </div>
        <div class="col-4">
          <input
            type="text"
            class="form-control"
            id="email"
            v-model="contact.email"
            placeholder="Enter Email"
            autocomplete="off"
          />
        </div>
        <div class="col-4">
          <input
            type="text"
            class="form-control"
            id="phone"
            v-model.number="contact.phone"
            placeholder="Enter Phone Number"
            autocomplete="off"
          />
        </div>
        <div class="col-6 offset-3 p-2">
          <button type="submit" class="btn btn-secondary w-100">
            Add Contact
          </button>
        </div>
      </div>
    </form>
  </div>
</template>
<script setup>
import { reactive } from "vue";

// const emit = defineEmits(["add-contact"]);

const props = defineProps({
  onAddContact: Function,
});
const contact = reactive({
  name: "",
  phone: "",
  email: "",
});

// function addContact() {
//   console.log(contact);
//   const contactData = {
//       ...contact
//   }
//   emit("add-contact", contactData);
//   contact.name = "";
//   contact.phone = "";
//   contact.email = "";
// }
function addContact() {
  const contactData = {
    ...contact,
  }
  props.onAddContact(contactData);
  contact.name = "";
  contact.phone = "";
  contact.email = "";
}
</script>
