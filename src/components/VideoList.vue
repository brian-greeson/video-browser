<template>
  <ul class="list-unstyled">
    <VideoItem v-for="video in videos" :video="video" :key="video.etag" @videoFocus="videoFocus"></VideoItem>
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
  methods: {
    videoFocus(video) {
      return this.$emit("videoFocus", video);
    },
  },
};
</script>

<style scoped>
ul {
  border: 5px, solid, black;
}
</style>