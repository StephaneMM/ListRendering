<template>
  <h1 class="text"><slot /></h1>
</template>
<script>
export default {};
</script>
<style scoped>
.text {
  font-family: "Work Sans";
  font-style: normal;
  font-weight: 400;
  font-size: 48px;
  line-height: 56px;

  max-width: 985px;
  width: 100%;

  padding: 0 40px;

  margin: 75px auto;
  text-align: left;
}
@media screen and (max-width: 450px) {
  .text {
    width: 174px;
    height: 28px;

    font-weight: 400;
    font-size: 24px;
    line-height: 28px;

    width: 100%;
    padding: 0 40px;

    margin: 70px auto 30px auto;

    text-align: left;
  }
}
</style>
