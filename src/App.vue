<template>
  <div>
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoList> </VideoList>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
const API_KEY = "AIzaSyAHrrNJZZFth5USadODeYniISqGpY_GK7k";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList
  },
  methods: {
    onTermChange: async function(searchTerm) {
      try {
        let response = await axios.get(
          "https://www.googleapis.com/youtube/v3/search",
          {
            params: {
              key: API_KEY,
              type: "video",
              part: "snippet",
              q: searchTerm
            }
          }
        );
        console.log(response);
      } catch (error) {
        throw new Error(error);
      }
    }
  }
};
</script>
