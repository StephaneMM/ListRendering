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
      console.log("clicked");
      this.$emit("changeDisplayMode");
    },
    icon() {
      return this.listView ? icons.list : icons.cards;
    },
  },
};
</script>

<style scoped>
.button {
  border: 0;
  display: flex;
  align-items: center;
  align-content: center;
  justify-content: center;
  justify-items: center;
  user-select: none;
  margin: 0.5rem;
}

button:hover {
  transform: scale(0.98) translateY(2px);
  opacity: 0.9;
  transition: transform 0.05s;
}
</style>
