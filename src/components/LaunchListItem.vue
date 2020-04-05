<template>
  <div>
      <p>{{ launch.mission_name }}</p>
      <button v-on:click="displayInfo">More Info &rarr;</button>
  </div>
</template>

<script>

import { eventBus } from "@/main.js";


export default {
    name: "launch-list-item",
    props: ["launch"],
    methods: {
        displayInfo: function() {
        eventBus.$emit("launch-selected", this.launch);
    },
    }
};
</script>

<style scoped>

</style>