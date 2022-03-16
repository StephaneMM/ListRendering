<template>
  <div class="button" @click="someoneClicked">
    <div class="img-container">
      <img :src="icon()" alt="icon" width="24" />
    </div>
  </div>
</template>

<script>
import icons from "../../resources/iconsPaths.js";

export default {
  name: "ListButton",

  props: {
    listView: {
      type: Boolean,
    },
  },


  methods: {
    someoneClicked() {
      this.isClicked = !this.isClicked;
      this.$emit("changeDisplayMode");
    },
    icon() {
      return this.listView ? icons.cards : icons.list;
    },
  },
};
</script>

<style scoped>
.button {
  border: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0.5rem;
}

</style>
