<template>
  <div v-if="video">
    <div>
      <iframe :src="videoUrl" />
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

<style lang="scss" scoped></style>
