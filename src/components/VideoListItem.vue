<template>
  <li @click="onVideoSelect">
    <img :src="thumbnailUrl" />
    <p>{{ videoTitle }}</p>
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
  },
  methods: {
    onVideoSelect() {
      this.$emit("videoSelect", this.video);
    }
  }
};
</script>

<style lang="scss" scoped>
li {
  padding: 1rem 2rem;
  border: 2px solid lightgray;
  border-radius: 10px;
  display: flex;
  align-items: center;
  cursor: pointer;

  &:not(:first-child) {
    margin-top: 1rem;
  }

  img {
    border-radius: 5px;
  }

  p {
    margin-left: 2rem;
    font-weight: 500;
  }

  &:hover {
    background-color: rgba(221, 221, 221, 0.9);
  }
}
</style>
