<template>
  <div class="bg-dark text pt-3">
    <div class="container">
      <div class="text-white float-end">
        Contact owner name: <input type="text" v-model="ownerName" />
      </div>
      <br /><br />
      <AddContact @add-contact="onAddContact($event)"></AddContact>
      <div class="row">
        <div class="col-12" v-for="contact in contacts" :key="contact.name">
          <Contact
            :name="contact.name"
            :phone="contact.phone"
            :email="contact.email"
            :ownerName="contact.ownerName"
            :isFavorite="contact.isFavorite"
            @update-favorite="
              contact.isFavorite = onUpdateFavorite($event, contact.phone)
            "
          ></Contact>
        </div>
      </div>
      <LuckyNumber :max-number="10"></LuckyNumber>
    </div>
  </div>
</template>

<script setup>
import { reactive, ref } from "vue";
import Contact from "./components/Contact.vue";
import AddContact from "./components/AddContact.vue";
import LuckyNumber from "./components/LuckyNumber.vue";

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

function onAddContact (contact) {
  contact.ownerName = ownerName.value;
  contact.isFavorite = false;
  console.log(contact);
  
  contacts.push(contact);
}

//***** Using Array  *****/
// function onUpdateFavorite(oldValueFromChildComponent, phoneNumberFromParentComponent) {
//   console.log(oldValueFromChildComponent); //return array of name and isfavorite
//   console.log(phoneNumberFromParentComponent); //coming from parent component

//   //Getting from child
//   return !oldValueFromChildComponent[0]; //return isFavorite only
// }

//***** Using Object  *****/
function onUpdateFavorite(
  oldValueFromChildComponent,
  phoneNumberFromParentComponent
) {
  console.log(oldValueFromChildComponent); //return array of name and isfavorite
  console.log(phoneNumberFromParentComponent); //coming from parent component

  //Getting from child
  return !oldValueFromChildComponent.isFavorite; //return isFavorite only
}
</script>

<style></style>
