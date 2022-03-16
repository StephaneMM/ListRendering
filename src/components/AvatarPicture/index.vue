<template>
  <div class="img-container" :style="cssVars">
    <img :src="image" alt="avatar-picture" class="img" />
  </div>
</template>

<script>
export default {
  name: "AvatarPicture",

  props: {
    image: {
      require: true,
      type: String,
    },
    pxSize: {
      require: true,
      type: Number,
      default: 80,
    },
  },

  computed: {
    windowWidth() {
      return window.innerWidth;
    },
    cssVars() {
      return {
        "--width": `${this.pxSize}px`,
        "--height": `${this.pxSize}px`,
      };
    },
  },
};
</script>

<style scoped>
.img-container {
  width: var(--width);
  height: var(--height);
  overflow: hidden;
  border-radius: 50%;
   box-shadow: 0px 5px 3px 0px rgba(0, 0, 0, 0.19);;
}

.img {
  width: 100%;
 
}

@media screen and (max-width: 830px) {
  .img-container {
    width: 80px;
    height: 80px;
  }

  .city {
    margin-bottom: 9px;
  }
}
</style>
