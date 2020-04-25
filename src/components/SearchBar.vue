<template>
  <div>
    <input type="text" @input="onInput" />
  </div>
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
  border: 2px solid rgb(182, 182, 182);
  border-radius: 10px;
  padding: 1rem;
  font-size: 1.4rem;
  width: 100%;
  outline: 0;
  &:focus {
    outline: 0.1rem dotted red;
  }
}
</style>
