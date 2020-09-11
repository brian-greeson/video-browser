<template>
  <div>
    <SearchBar @searchChange="search"></SearchBar>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar";
export default {
  name: "App",
  components: {
    SearchBar,
  },
  methods: {
    search: function (query) {
      console.log("got a new search: " + query);
    },
  },
};
</script>