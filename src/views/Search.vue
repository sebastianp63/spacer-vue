<template>
  <div class="wrapper">
    <Claim></Claim>
    <SearchInput/>
      <ul>
        <li v-for="item in results" :key="item.data[0].nasa_id">
          <p>{{item.data[0].description}}</p>
        </li>
      </ul>
  </div>
</template>

<script>
const axios = require("axios");
const debounce = require("lodash.debounce");
const API = `https://images-api.nasa.gov`;

import Claim from "@/components/Claim.vue"
import SearchInput from "@/components/SearchInput.vue"
export default {
  name: "Search",
  data() {
    return {
      searchValue: "",
      results: []
    };
  },
  methods: {
    eventHandler: debounce(function() {
      axios
        .get(`${API}/search?q=${this.searchValue}&media_type=image`)
        .then(response => {
          console.log(response.data.collection.items);
          this.results = response.data.collection.items;
        })
        .catch(error => {
          console.log(error);
        });
    }, 500)
  },
  components: {
    Claim,
    SearchInput
  }
};
</script>


<style lang="scss" scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin: 0;
  padding: 30px;
  width: 100%;
  height: 100vh;
  background-image: url("../assets/heroimage.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 80% 0;
}


</style>
