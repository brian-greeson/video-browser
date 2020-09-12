<template>
  <ul class="list-group">
    <VideoItem v-for="video in videos" :video="video" :key="video.etag"></VideoItem>
  </ul>
</template>

<script>
import VideoItem from "./VideoItem";

export default {
  name: "VideoList",
  components: {
    VideoItem,
  },
  props: {
    videos: Array,
  },
};
</script>

<style scoped>
ul {
  border: 5px, solid, black;
}
</style>