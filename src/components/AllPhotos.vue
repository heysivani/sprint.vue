<template>
  <div class="allPhotos"
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
  props: ['convertedPhotos'],
};
</script>

<style></style>
