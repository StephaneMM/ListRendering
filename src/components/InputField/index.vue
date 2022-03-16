<template>
  <div class="input-container">
    <img src="/icons/Vector.png" height="18" />
    <input
      class="input"
      type="text"
      @input="input"
      placeholder="Search a contact"
      size="80"
    />
  </div>
</template>

<script>
export default {
  name: "InputField",

  props: {
    listView: {
      type: Boolean,
    },
  },
  methods: {
    input(e) {
      console.log(e.target.value);
      this.$emit("useSearch", e.target.value);
    },
  },
};
</script>

<style scoped>
.input {
  border: none;
  margin-left: 0.5rem;
  background-color: var(--background);
  /* width: 100%; */
}
.input-container {
  display: flex;
  align-items: center;
  margin-left: 13.5px;
  padding: 6px 0;

  width: 100%;
  max-width: 300px;
  height: 2rem;

  border-bottom: 2px solid black;
}

@media screen and (max-width: 450px) {
  .input {
    width: 100%;
  }

  .input-container {
    width: 100%;
    /* max-width: 0; */
    height: 2rem;
    margin-left: 0px;
    margin-bottom: 30px;

    border-bottom: 2px solid black;
  }
}
</style>
