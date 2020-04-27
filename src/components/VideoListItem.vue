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
  border-radius: 10px;
  border-top: 1px solid white;
  border-bottom: 1px solid white;
  display: flex;
  align-items: center;
  cursor: pointer;
  transition: border 400ms ease;

  &:not(:first-child) {
    margin-top: 1rem;
  }

  img {
    border-radius: 10px;
  }

  p {
    margin-left: 2rem;
    font-weight: 500;
    color: white;
    line-height: 1.4;
  }

  &:hover {
    border-top: 1px solid rgb(81, 240, 237);
    border-bottom: 1px solid rgb(81, 240, 237);
  }
}
</style>
