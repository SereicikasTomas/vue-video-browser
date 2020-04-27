<template>
  <div class="video-detail" v-if="video">
    <div class="video" style="padding-top: 56.25%;">
      <iframe :src="videoUrl" frameborder="0" allowfullscreen />
    </div>
    <div class="details">
      <h2>{{ video.snippet.title }}</h2>
      <p>{{ video.snippet.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "videoDetail",
  props: ["video"],
  computed: {
    videoUrl() {
      const { videoId } = this.video.id;
      return `https://www.youtube.com/embed/${videoId}`;
    }
  }
};
</script>

<style lang="scss" scoped>
.video-detail {
  grid-row: 2 / 3;
  grid-column: 1 / 2;
}
.video {
  position: relative;
  iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border-radius: 10px;
  }
}
.details {
  margin-top: 2rem;
  padding: 1rem 2rem;
  border: 2px solid lightgray;
  border-radius: 10px;
  h2 {
    margin-bottom: 2rem;
  }
}
</style>
