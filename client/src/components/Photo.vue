<template>
  <v-img
    contain
    :src="require(`../assets/images/${photo.filename}`)"
    aspect-ratio="2"
  >
    <template v-slot:placeholder>
      <v-row class="fill-height ma-0" align="center" justify="center">
        <v-progress-circular
          indeterminate
          color="grey lighten-5"
        ></v-progress-circular>
      </v-row>
    </template>
  </v-img>
</template>

<script>
export default {
  name: "photo",
  props: {
    photo: Object
  }
};
</script>
