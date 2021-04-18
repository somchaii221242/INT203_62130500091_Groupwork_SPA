<template>
  <div class="flex">
    <div class="mx-auto">
    <h1 class="px-44">My Profile</h1>
    <img src="@/assets/suit.jpg" />
    <p class="px-44">Name : Somchai Chasa</p>
    <p class="px-44">ID : 62130500091</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "about",
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
