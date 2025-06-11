<template>
  <div class="bg-dark text pt-3" :style="{ height: '100vh' }">
    <div class="container">
      <div class="row text-white p-2 mb-2">
        <div class="col-6">
          Owner name : <input type="text" v-model="ownerName" />
        </div>
        <div class="col-6 text-end">
          Max Lucky Number : <input type="number" v-model="maxNumber" />
        </div>
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
            :maxLuckyNumber="maxNumber"
            @update-favorite="
              contact.isFavorite = onUpdateFavorite($event, contact.phone)
            "
          ></Contact>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive, ref } from "vue";
import Contact from "./components/Contact.vue";
import AddContact from "./components/AddContact.vue";

const ownerName = ref("masteryVue");
const maxNumber = ref(100);

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

function onAddContact(contact) {
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
