<template>
  <div class="about" >
  <h1 class="text-center">{{msg}}</h1>
  </div>
</template>

<script>
export default {
  name: "about",
  props: {
    msg: String
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
