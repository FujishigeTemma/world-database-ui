<template>
  <div>
    <div v-if="countryList">{{ countryList }}</div>
    <div v-else>リストが取得できませんでした</div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Country",
  data() {
    return {
      countryList: null
    };
  },
  mounted() {
    const cityName = this.$route.params.cityName;
    axios.get("/api/cities/" + cityName).then(res => {
      this.countryList = res.data;
    });
  }
};
</script>
