<template>
  <input placeholder="Search for a video..." type="text" @input="onInput" />
</template>

<script>
export default {
  name: "SearchBar",
  methods: {
    onInput: function(event) {
      this.$emit("termChange", event.target.value);
    }
  }
};
</script>

<style lang="scss" scoped>
input {
  background: transparent;
  border: none;
  border-bottom: 1px solid white;
  color: white;
  border-radius: 10px;
  padding: 1rem 2rem;
  font-size: 1.4rem;
  width: 100%;
  outline: 0;
  letter-spacing: 1px;
  &::placeholder {
    color: white;
  }
  grid-column: 1 / 3;
}
</style>
