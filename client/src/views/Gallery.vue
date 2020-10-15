<template>
  <v-container fluid>
    <v-row justify="space-around">
      <v-col
        :cols="12 / itemsPerRow"
        v-for="(photo, index) in photos"
        :key="index"
        class="d-flex child-flex"
        @click="openPhoto(photo)"
      >
        <photo :photo="photo"></photo>
      </v-col>
    </v-row>
    <v-dialog v-model="openDialog">
      <dialog-photo :photos="photos" :photo="selectedPhoto" @close="closePhoto" />
    </v-dialog>
  </v-container>
</template>

<script>
import Photo from "@/components/Photo";
import DialogPhoto from "@/components/DialogPhoto";

export default {
  name: "Gallery",
  data() {
    return {
      selectedPhoto: {},
      openDialog: false
    };
  },
  computed: {
    itemsPerRow() {
      switch (this.$vuetify.breakpoint.name) {
        case "xs":
        case "sm":
          return 2;
        case "md":
          return 3;
        case "lg":
          return 4;
        case "xl":
          return 6;
        default:
          return 6;
      }
    },
    photos() {
      return require("../photos.json");
    }
  },
  methods: {
    openPhoto(photo) {
      this.selectedPhoto = photo;
      this.openDialog = true;
    },
    closePhoto() {
      this.openDialog = false;
    }
  },
  components: {
    Photo,
    DialogPhoto
  }
};
</script>
