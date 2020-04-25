<template>
  <div class="app">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoList @videoSelect="onVideoSelect" :videos="videos"> </VideoList>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList
  },
  data() {
    return {
      videos: []
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
      console.log(video);
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
}

.app {
  max-width: 100rem;
  height: 50vh;
  margin: auto;
  margin-top: 10vh;
}
</style>
