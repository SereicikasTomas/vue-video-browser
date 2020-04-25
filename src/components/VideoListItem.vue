<template>
  <li>
    <img :src="video.snippet.thumbnails.default.url" />
    {{ video.snippet.title }}
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: ["video"]
};
</script>

<style lang="scss" scoped>
li {
  margin-top: 0.5rem;
  padding: 1rem;
  border: 1px solid lightblue;
}
</style>
