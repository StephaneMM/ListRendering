<template>
  <div class="button" @click="someoneClicked">
    <div class="img-container">
      <img src="/icons/Sorting-icon.png" alt="icon" width="32" />
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
  justify-content: center;

  top: 4px;
}

</style>
