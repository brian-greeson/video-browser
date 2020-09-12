<template>
  <a :href="videoUrl" class="list-group-item list-group-item-action">
    <img class="img-thumbnail" :src="thumbnailUrl" />
    {{ videoTitle }}
  </a>
</template>

<script>
export default {
  name: "VideoItem",
  props: ["video"],
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    },
    videoUrl() {
      return "www.youtube.com/" + this.video.id.videoId;
    },
    videoTitle() {
      return this.video.snippet.title;
    },
  },
};
</script>

