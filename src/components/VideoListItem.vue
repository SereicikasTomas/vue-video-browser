<template>
  <li>
    <img :src="thumbnailUrl" />
    <h4>{{ videoTitle }}</h4>
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
  padding: 1rem 2rem;
  border: 2px solid lightgray;
  border-radius: 10px;
  display: flex;
  cursor: pointer;

  img {
    border-radius: 5px;
  }

  h4 {
    margin-left: 2rem;
    font-weight: 500;
  }

  &:hover {
    background-color: rgba(221, 221, 221, 0.9);
  }
}
</style>
