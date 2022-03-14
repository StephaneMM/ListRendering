<template>
  <div class="img-container">
    <img :src="image" alt="avatar-picture" class="img" style="" />
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
      type: String,
    },
  },
};
</script>

<style scoped>
.img-container {
  width: 100px;
  height: 100px;
  overflow: hidden;
  border-radius: 50%;
}

.img {
  width: 100%;
}
</style>
