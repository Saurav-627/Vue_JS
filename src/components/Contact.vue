<template>
  <div class="bg-info rounded p-1 pb-4 m-2">
    <div class="row">
      <div class="col-6">
        <h1>Name : {{ name }}</h1>
        <p>Email : {{ email }}</p>
        <p>Phone : {{ phone }}</p>
      </div>
      <div class="col-3">
        <button @click="toggleFavorite" :class="[isFavorite ? 'btn btn-warning' : 'btn btn-success']">
          {{ isFavorite ? "Remove from" : "Add to" }} Favorite
        </button>

        <!-- Using inLine Emit -->
        <!-- <button
          @click="
            emit('update-favorite', {
              name: props.name,
              isFavorite: props.isFavorite,
            })
          "
          :class="[isFavorite ? 'btn btn-warning' : 'btn btn-success']"
        >
          {{ isFavorite ? "Remove from" : "Add to" }} Favorite
        </button> -->
      </div>
    </div>
    <span class="float-end small" v-if="ownerName != ''">
      "this contact info belongs to {{ ownerName }}"
    </span>
  </div>
</template>

<script setup>
// const email = ref("hsaurav@gmail"); //if email is passed from app then this will work not props email

// const props = defineProps(["name","phone","ownerName"]); //Not Validated

const props = defineProps({
  name: { type: String, required: true }, //validating props
  phone: Number, //validating props
  email: { type: String, required: true }, //validating props
  ownerName: String, //validating props
  isFavorite: Boolean,
});

const emit = defineEmits(["update-favorite"]); //to trigger from child to parent

// function toggleFavorite() {
//   emit("update-favorite", [props.isFavorite, props.name]); //using array
// }

//using Object
function toggleFavorite() {
  emit("update-favorite", {
    name: props.name,
    isFavorite: props.isFavorite,
  });
}
</script>
