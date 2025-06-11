<!-- Passing Method as a props in child component.

Function define in parent:

function onAddContact(contact) {
    contact.ownerName = ownerName.value;
    contact.isFavorite = false;
    console.log(contact);
  
    contacts.push(contact);
  }

Passing Props:

<AddContact :onAddContact="onAddContact"></AddContact>

Accessing in child component:

const props = defineProps({
    onAddContact: Function,
});

using it:
function addContact() {
    const contactData = {
      ...contact,
    }
    props.onAddContact(contactData);
    contact.name = "";
    contact.phone = "";
    contact.email = "";
} -->