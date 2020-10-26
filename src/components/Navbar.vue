<template>
  <div>
    <input type="button" id="homeButt" v-on:click="$emit('home')"
      value="Home" />
    <upload 
    @save-file="saveFile" />
  </div>
</template>

<script>
import Upload from "./Upload";
import { saveObject } from "../../utils/index.js";

export default {
  name: "Navbar",
  components: {
    upload: Upload,
  },
  props: ["updatePhotos"],
  methods: {
    async saveFile (file) {
      console.log("file in saveFile", file[0]);
      const savedFile = await saveObject(file[0]);
      console.log("saved file ", savedFile);
    }
  }
};
</script>

<style>
  
</style>
