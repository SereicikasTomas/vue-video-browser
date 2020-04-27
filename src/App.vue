<template>
  <div class="app">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoDetail :video="selectedVideo" />
    <VideoList @videoSelect="onVideoSelect" :videos="videos"> </VideoList>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetail from "./components/VideoDetail";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data() {
    return {
      videos: [],
      selectedVideo: null
    };
  },
  methods: {
    onTermChange: async function(searchTerm) {
      try {
        let response = await axios.get(
          "https://www.googleapis.com/youtube/v3/search",
          {
            params: {
              key: process.env.VUE_APP_API_KEY,
              type: "video",
              part: "snippet",
              q: searchTerm
            }
          }
        );
        this.videos = response.data.items;
      } catch (error) {
        console.error(error);
      }
    },
    onVideoSelect(video) {
      this.selectedVideo = video;
    }
  }
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

html {
  font-size: 62.5%;
  font-family: Arial, Helvetica, sans-serif;
  background: linear-gradient(0deg, rgb(38, 84, 112), rgb(255, 255, 255))
    no-repeat fixed center;
}

h2 {
  font-size: 2.5rem;
}

p {
  font-size: 1.4rem;
}

.app {
  max-width: 120rem;
  height: 50vh;
  margin: auto;
  display: grid;
  grid-template-rows: min-content auto;
  grid-template-columns: 3fr 2fr;
  gap: 2rem;
  padding: 2rem;
}

@media only screen and (max-width: 56.25em) {
  .app {
    grid-template-columns: 1fr;
    row-gap: 2rem;
    column-gap: 0;
  }
}
</style>
