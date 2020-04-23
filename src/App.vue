<template>
  <div>
    <SearchBar @termChange="onTermChange"></SearchBar>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
const API_KEY = "AIzaSyAHrrNJZZFth5USadODeYniISqGpY_GK7k";

export default {
  name: "App",
  components: {
    SearchBar
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
