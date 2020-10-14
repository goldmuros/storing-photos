<template>
  <div class="modalDialog">
    <button class="close" @click="close">X</button>
    <v-img class="image ma-0" contain :src="image" />
    <v-row class="white--text align-center ml-2">
      <v-col cols="4">Author: {{ photo.author }}</v-col>
      <v-col cols="4">Camera: {{ photo.camera }}</v-col>
      <v-col cols="4">Hashtag: {{ photo.hashtag }}</v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: "DialogPhoto",
  props: {
    openDialog: Boolean,
    photo: Object
  },
  data() {
    return {
      image: require(`../assets/images/${this.photo.filename}`)
    };
  },
  methods: {
    close() {
      this.$emit("close");
    }
  }
};
</script>

<style scoped>
.modalDialog {
  position: fixed;
  font-family: Arial, Helvetica, sans-serif;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  background: rgba(0, 0, 0, 0.8);
  opacity: 1;
  -webkit-transition: opacity 400ms ease-in;
  -moz-transition: opacity 400ms ease-in;
  transition: opacity 400ms ease-in;
  pointer-events: auto;
}

.headerModal {
  display: flex;
  justify-content: right;
}

.close {
  float: right;
  padding: 10px 10px;
  color: white;
  background: red;
}

.image {
  margin: 10px;
  max-width: 90%;
  max-height: 90%;
}
</style>
