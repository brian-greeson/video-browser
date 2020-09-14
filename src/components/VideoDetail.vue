<template>
  <div v-if="video">
    <div class="embed-responsive embed-responsive-16by9">
      <iframe :src="videoId"></iframe>
    </div>
  </div>
</template>

<script>
export default {
  name: "VideoDetail",
  props: ["video"],
  computed: {
    videoId() {
      return "https://www.youtube.com/embed/" + this.video.id.videoId;
    },
  },
};
</script>

<style>
iframe {
  height: 100%;
  width: auto;
}
</style>