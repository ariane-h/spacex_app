<template>
  <div>
      <h3>Filter by past/upcoming launches</h3>
      <select id="launch-status" v-model="launchStatusResult" @change="selectedLaunches" >
          <option disabled value="">Select Status</option>
          <option :value="launches">All</option>
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
            launchStatusResult: [], 
        };
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
            eventBus.$emit('launch-status', this.launchStatusResult)
        }
    },
}
</script>

<style>

</style>