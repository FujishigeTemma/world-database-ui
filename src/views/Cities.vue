<template>
  <div>
    <div v-if="cityList">
      <div v-for="city in cityList" :key="city.Name">
        <div class="Name">
          <router-link :to="`/city/${city.Name}`">
            {{ city.Name }}
          </router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "CityList",
  data() {
    return {
      cityList: null
    };
  },
  mounted() {
    const countryName = this.$route.params.countryName;
    axios.get("/api/countries/" + countryName).then(res => {
      this.cityList = res.data;
    });
  }
};
</script>
<style>
div.Name {
  display: flex;
  justify-content: center;
}
</style>
