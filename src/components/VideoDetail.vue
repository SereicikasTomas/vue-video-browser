<template>
  <div>
    {{ video.snipped.title }}
  </div>
</template>

<script>
export default {
  name: "videoDetail",
  props: ["video"]
};
</script>

<style lang="scss" scoped></style>
