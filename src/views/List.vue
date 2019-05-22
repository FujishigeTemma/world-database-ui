<template>
  <div>
    <div class="body">
      <div v-if="countryList">
        <div v-for="Country in countryList" :key="Country.Name">
          <div class="Country">
            <div class="Name">
              <router-link :to="`/countries/${Country.Name}`">{{
                Country.Name
              }}</router-link>
            </div>
            <div class="Continent">--{{ Country.Continent }}--</div>
            <div class="Region">{{ Country.Region }}</div>
          </div>
        </div>
      </div>
      <div v-else>リストが取得できませんでした</div>
    </div>
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
    axios.get("/api/countryList").then(res => {
      this.countryList = res.data;
    });
  }
};
</script>

<style>
div.Country {
  display: flex;
  justify-content: center;
}
div.body {
  display: flex;
  justify-content: center;
}
</style>
