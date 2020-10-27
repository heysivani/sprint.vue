<template>
  <div>
    <input type="button" id="homeButt" v-on:click="$emit('home')"
      value="Home" />
    <Upload 
    @save-file="saveFile" />
  </div>
</template>

<script>
import Upload from "./Upload";
import { saveObject } from "../../utils/index.js";

export default {
  name: "Navbar",
  components: {
    Upload: Upload,
  },
  props: ["updatePhotos"],
  methods: {
    async saveFile (file) {
      const savedFile = await saveObject(file[0]);
      this.updatePhotos(savedFile);
    }
  }
};
</script>

<style>
  
</style>
