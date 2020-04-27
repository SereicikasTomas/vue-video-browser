<template>
  <ul>
    <VideoListItem
      :key="video.etag"
      v-for="video in videos"
      :video="video"
      @videoSelect="onVideoSelect"
    >
    </VideoListItem>
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem";

export default {
  name: "VideoList",
  components: {
    VideoListItem
  },
  props: ["videos"],
  methods: {
    onVideoSelect(video) {
      this.$emit("videoSelect", video);
    }
  }
};
</script>

<style lang="scss" scoped>
ul {
  font-size: 1.8rem;
  list-style: none;
  grid-row: 2 / 3;
  grid-column: 2 / 3;
}

@media only screen and (max-width: 56.25em) {
  ul {
    grid-row: 3 / 4;
    grid-column: 1 / 2;
  }
}
</style>
