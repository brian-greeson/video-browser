<template>
  <div class="container">
    <div class="jumbotron">
      <div class="row">
        <img
          class="align-self-center mr-3 logo-icon"
          src="https://github.com/brian-greeson/video-browser/raw/master/public/yt_icon_rgb.png"
        />
        <h1 class="display-3">ZenTube</h1>
      </div>
      <p class="lead">Minimalist Youtube Search</p>
      <hr class="my-7" />
      <p class="lead">
        <SearchBar @searchChange="onSearchChange"></SearchBar>
      </p>
    </div>

    <div class="row">
      <div class="col-8">
        <VideoDetail :video="currentVideo"></VideoDetail>
      </div>
      <div class="col-4">
        <VideoList v-bind:videos="videoResults" @videoFocus="videoFocus"></VideoList>
      </div>
    </div>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetail from "./components/VideoDetail";

import axios from "axios";
const YOUTUBE_KEY = process.env.VUE_APP_YOUTUBE_KEY;

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
    VideoDetail,
  },
  data() {
    return {
      videoResults: [],
      currentVideo: Object,
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
          this.videoResults = response.data.items;
        });
    },
    videoFocus(video) {
      this.currentVideo = video;
    },
  },
};
</script>

<style scoped>
.logo-icon {
  height: 50px;
  width: auto;
}
</style>