<template>
  <div class="text-center">
    <h2 class="text-3xl font-bold">
      {{ text }}
    </h2>
    <div class="text-2xl mt-4 mb-10">{{ timestamp }}</div>
  </div>
</template>

<script>
import { DateTime } from "luxon";

export default {
  name: "DataTitle",
  props: ["text", "dataDate"],
  computed: {
    timestamp: function () {
      return DateTime.fromISO(this.dataDate).toLocaleString(
        DateTime.DATETIME_FULL
      );
    },
  },
};
</script>
