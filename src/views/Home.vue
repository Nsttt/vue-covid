<template>
  <main v-if="!loading">
    <DataTitle :text="title" :dataDate="dataDate" />
  </main>
  <main class="flex flex-col align-center justify-center text-center" v-else>
</template>

<script>
import DataTitle from "../components/DateTitle.vue";
import axios from "axios";

export default {
  name: "Home",
  components: {
    DataTitle,
  },
};
</script>
