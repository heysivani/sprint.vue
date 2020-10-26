<template>
  <div>
    <input type="button" id="homeButt" v-on:click="$emit('home')"
      value="Home" />
    <upload />
  </div>
</template>

<script>
import Upload from "./Upload";

export default {
  name: "Navbar",
  components: {
    upload: Upload,
  },
};
</script>

<style>
  
</style>
