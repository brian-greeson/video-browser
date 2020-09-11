<template>
  <div>
    <input @input="onInput" />
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

<style>
</style>