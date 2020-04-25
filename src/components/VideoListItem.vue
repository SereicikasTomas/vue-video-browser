<template>
  <li>
    <img :src="thumbnailUrl" />
    {{ videoTitle }}
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: ["video"],
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    },
    videoTitle() {
      return this.video.snippet.title;
    }
  }
};
</script>

<style lang="scss" scoped>
li {
  margin-top: 0.5rem;
  padding: 1rem;
  border: 1px solid lightblue;
}
</style>
