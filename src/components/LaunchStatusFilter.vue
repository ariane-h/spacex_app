<template>
  <div>
      <h3>Filter by past/upcoming launches</h3>
      <select id="launch-status" v-model="selectedStatus" @change="selectLaunchStatus">
          <option disabled value="">Select</option>
          <option value="true">Upcoming</option>
          <option value="false">Past</option>
      </select>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";

export default {
    name: "launch-status-filter",
    data(){
        return{
            selectedStatus: null,
        }
    },
    methods: {
        selectLaunchStatus: function(){
            eventBus.$emit('launch-status', this.selectedStatus)
        }
    },
}
</script>

<style>

</style>