<template>
  <div>
    <SearchBar @searchChange="onSearchChange"></SearchBar>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar";

export default {
  name: "App",
  data() {
    return {
      apiKey: process.env.VUE_APP_YOUTUBE_KEY,
    };
  },
  components: {
    SearchBar,
  },
  methods: {
    onSearchChange(query) {
      console.log("got a new search: " + query);
    },
  },
};
</script>