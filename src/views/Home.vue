<template>
  <main v-if="!loading">
    <DataTitle :text="title" :dataDate="dataDate" />
  </main>
  <main class="flex flex-col align-center justify-center text-center" v-else>
    <div class="text-gray-500 text-3xl mt-10 mb-6">Fetching Data</div>
    <p class="w-24 m-auto">⏳</p>
  </main>
</template>

<script>
import DataTitle from "../components/DateTitle.vue";
import axios from "axios";

export default {
  name: "Home",
  components: {
    DataTitle,
  },
  data() {
    return {
      loading: true,
      title: "Global",
      dataDate: "",
      stats: {},
      countries: [],
      loadingImage: "",
    };
  },
  methods: {
    async fetchCovidData() {
      const res = await axios.get("https://api.covid19api.com/summary");
      return res.data;
    },
  },
  async created() {
    const data = await this.fetchCovidData();
    this.dataDate = data.Date;
    this.stats = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  },
};
</script>
