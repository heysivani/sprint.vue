<template>
  <div>
     <input type="file" @change="onChange"/>
     <input type="submit" id="uploadButt" value="Upload"
     v-on:click="$emit('save-file', [file])"
    />
  </div>
</template>

<script>
export default {
  name: "Upload",
  data: () => ({
    file: null,
  }),
  methods: {
    onChange(event) {
      this.file = event.target.files[0];
      console.log("file", this.file);
    }
  }
};
</script>

<style></style>
