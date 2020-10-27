<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <h1>{{ title }}</h1>
    <Navbar 
      @home="goHome" :updatePhotos="updatePhotos"
    />
    <template v-if="currentView==='allPhotos'">
      <AllPhotos />
    </template>
    <template v-if="currentView==='singlePhoto'">
      <SinglePhoto />
    </template>
  </div>
</template>

<script>
import Navbar from "./components/Navbar";
import AllPhotos from "./components/AllPhotos";
import SinglePhoto from "./components/SinglePhoto";
import { listObjects, getSingleObject } from "../utils/index.js";

export default {
  name: "App",
  components: {
    Navbar: Navbar,
    AllPhotos: AllPhotos,
    SinglePhoto: SinglePhoto,
  },
  data: () => ({
    title: "Photo Upload App",
    currentView: "allPhotos",
    photos: [],
    convertedPhotos: [],
    selectedPhoto: "",
  }),
  created() {
    listObjects()
      .then( promisedImages => {
        this.photos = promisedImages;
      })
      .then( photos => {
        this.convertToBase()
      })
  },
  methods: {
    goHome() {
      this.currentView = "allPhotos";
    },
    updatePhotos(file) {
      this.photos.push(file);
      this.convertToBase();
    },
    async convertToBase() {
      let promises = this.photos.map(photo => getSingleObject(photo.Key));
      this.convertedPhotos = await promises;
    }
  }
};
</script>

<style>
#app {
  text-align: center;
}
</style>
