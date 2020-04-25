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
}
</style>
