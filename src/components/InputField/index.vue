<template>
  <div class="input-container">
    <img src="/icons/Vector.png" height="18" />
    <input
      class="input"
      type="text"
      @input="input"
      placeholder="Search a contact"
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
  margin-left: 16px;
  background-color: var(--background);
}
.input-container {
  display: flex;
  margin-left: 1rem;
  padding: 6px 0;
  height: 1rem;
  border-bottom: 2px solid black;
}
</style>
