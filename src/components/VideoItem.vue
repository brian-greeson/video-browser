<template>
  <li class="list-group-item media" @click="onVideoSelect">
    <img class="mr-3" :src="thumbnailUrl" />
    <div class="media-body">{{ videoTitle }}</div>
  </li>
</template>

<script>
export default {
  name: "VideoItem",
  props: ["video"],
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    },
    videoTitle() {
      return this.video.snippet.title;
    },
  },
  methods: {
    onVideoSelect() {
      this.$emit("videoFocus", this.video);
    },
  },
};
</script>

<style scoped>
li {
  display: flex;
  cursor: pointer;
}

li:hover {
  background-color: lightgray;
}
</style>

