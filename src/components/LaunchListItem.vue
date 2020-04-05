<template>
  <div>
      <div class="launch-list-item">
        <div><p>{{ launch.mission_name }}</p></div>
        <div class="more-info-button"><button v-on:click="displayInfo">More Info &rarr;</button></div>
      </div>
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
.launch-list-item{
    display: flex;
    flex-direction: row;
}

.more-info-button{
    align-self: center;
    padding-left: 10px;
}

</style>