<template>
  <div class="allPhotos">
      <img v-for="(photo, index) in convertedPhotos"
        :key="index"
        :src="`data:image/*;base64,${photo}`"
        v-on:click="$emit('select-photo', [index])"
      />
  </div>
</template>

<script>
export default {
  name: "AllPhotos",
  props: ['convertedPhotos'],
};
</script>

<style>
img {
  max-height: 200px;
  max-width: auto;
  cursor: pointer;
}
</style>
