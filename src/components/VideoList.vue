<template>
  <ul>
    <VideoListItem :key="video.etag" v-for="video in videos" :video="video">
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
  props: ["videos"]
};
</script>

<style lang="scss" scoped>
ul {
  font-size: 1.8rem;
  list-style: none;
}
</style>
