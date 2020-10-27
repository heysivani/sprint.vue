<template>
  <div class="singlePhoto">
  <img :src='selectedPhoto'/>
  </div>
</template>

<script>
export default {
  name: "SinglePhoto",
  props: ['selectedPhoto']
};
</script>

<style></style>
