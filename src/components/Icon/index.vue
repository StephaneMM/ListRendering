<template>
  <div class="button" @click="someoneClicked">
    <div class="img-container">
      <img :src="icon" :alt="alt" :width="pxWidth" />
    </div>
  </div>
</template>

<script>
// import icons from './resources/iconsPaths.js'

export default {
  name: "Icon",

  props: {
    icon: {
      require: true,
      type: String,
    },
    associatedFunctionName: {
      type: String,
    },
    alt: {
      type: String,
      default: "icon",
    },

    pxWidth: {
      type: Number,
      default: 20,
    },
  },
  methods: {
    someoneClicked() {
      this.$emit(this.associatedFunctionName);
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
  margin: 5px;

  padding: 0;
}
</style>
