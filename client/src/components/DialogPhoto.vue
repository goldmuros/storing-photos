<template>
  <v-card dark>
    <v-card-title>
      <v-spacer></v-spacer>
      <v-btn icon dark right color="red" @click="close">
        <v-icon>mdi-close</v-icon>
      </v-btn>
    </v-card-title>
    <v-card-text>
      <v-carousel hide-delimiters :continuous="false" v-model="photo.id">
        <v-carousel-item
          v-for="item in photos"
          :key="item.id"
          :src="require(`../assets/images/${item.filename}`)"
        ></v-carousel-item>
      </v-carousel>
      <!-- <v-img :src="require(`../assets/images/${this.photo.filename}`)" /> -->
    </v-card-text>
    <v-btn
      fab
      dark
      absolute
      bottom
      right
      color="red"
      class="mb-9 pb-0"
      @click="openShareURL = !openShareURL"
    >
      <v-icon>mdi-share-variant</v-icon>
    </v-btn>
    <v-dialog v-model="openShareURL" max-width="50%">
      <v-card dark class="pt-4">
        <v-card-text>
          <v-text-field
            v-model="shareURL"
            :append-outer-icon="'mdi-content-copy'"
            filled
            disabled
            type="text"
          ></v-text-field>
        </v-card-text>
      </v-card>
    </v-dialog>
    <v-footer absolute dark>
      <v-row class="white--text align-center ml-2">
        <v-col cols="4">Author: {{ photo.author }}</v-col>
        <v-col cols="4">Camera: {{ photo.camera }}</v-col>
        <v-col cols="4">Hashtag: {{ photo.hashtag }}</v-col>
      </v-row>
    </v-footer>
  </v-card>
</template>

<script>
export default {
  name: "DialogPhoto",
  props: {
    openDialog: Boolean,
    photo: Object,
    photos: Array
  },
  data() {
    return {
      openShareURL: false,
      shareURL: this.photo.filename
    };
  },
  methods: {
    close() {
      this.$emit("close");
    }
  }
};
</script>
