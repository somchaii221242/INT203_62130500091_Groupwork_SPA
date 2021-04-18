<template>
  <div class="home " >
  <h1 class="text-center">{{msg}}</h1>
  </div>
</template>

<script>
export default {
  name: "homepage",
  props: {
    msg: String
  }
};
</script>


