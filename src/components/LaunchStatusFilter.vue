<template>
  <div>
      <h3>Filter by past/upcoming launches</h3>
      <select id="launch-status" v-model="launchesByStatus" @change="selectedLaunches" >
          <option disabled value="">Select</option>
          <option :value="upcomingLaunches">Upcoming</option>
          <option :value="pastLaunches">Past</option>
      </select>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";

export default {
    name: "launch-status-filter",
    props: ["launches"],
    data(){
        return{
            launchesByStatus: null,
        }
    },
    computed: {
        upcomingLaunches: function(){
            return this.launches.filter((launch) => launch.upcoming)
        },
        pastLaunches: function(){
            return this.launches.filter((launch) => !launch.upcoming)
        }
    },
    methods: {
        selectedLaunches: function(){
            eventBus.$emit('launch-status', this.launchesByStatus)
        }
    },
}
</script>

<style>

</style>