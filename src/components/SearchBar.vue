<template>
  <div>
    <label for="search-bar">Query + Enter</label>
    <input class="ml-3" id="search-bar" @keyup.enter="onInput" />
  </div>
</template>

<script lang="ts">
export default {
  name: "SearchBar",
  methods: {
    onInput: function (event) {
      this.$emit("searchChange", event.target.value);
    },
  },
};
</script>

<style scoped>
input {
  width: 75%;
}

div {
  text-align: center;
  margin: 10px;
}
</style>>

