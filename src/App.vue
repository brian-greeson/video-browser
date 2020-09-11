<template>
  <div>
    <SearchBar @searchChange="onSearchChange"></SearchBar>
    <VideoList></VideoList>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import axios from "axios";
const YOUTUBE_KEY = process.env.VUE_APP_YOUTUBE_KEY;
export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
  },
  data: function () {
    return {
      searchResults: {},
    };
  },
  methods: {
    onSearchChange(query) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search/", {
          params: {
            key: YOUTUBE_KEY,
            type: "video",
            maxResults: 10,
            part: "snippet",
            q: query,
          },
        })
        .then((response) => {
          this.searchResults = response.data.items;
        });
    },
  },
};
</script>