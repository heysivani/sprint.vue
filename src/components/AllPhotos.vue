<template>
  <div class="allPhotos"
    v-if="convertedPhotos.length"
    >This is all photos
      <img v-for="(photo, index) in convertedPhotos"
        :key="index"
        :src="`data:image/*;base64,${photo}`"
      />
  </div>
</template>

<script>
export default {
  name: "AllPhotos",
  props: ["convertedPhotos"],
  methods: {
    renderImages() {
      console.log("Rendered!", this.convertedPhotos);
    }
  }
};
</script>

<style></style>
