<template>
  <div class="button" @click="someoneClicked">
    <div class="img-container">
      <img src="/icons/Sorting-icon.png" alt="icon" width="18" />
    </div>
  </div>
</template>

<script>
// import icons from './resources/iconsPaths.js'

export default {
  name: "SortButton",

  methods: {
    someoneClicked() {
      this.$emit("sortContacts");
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
}

button:enabled:active {
  transform: scale(0.98) translateY(2px);
  opacity: 0.9;
  transition: transform 0.05s;
}
</style>
