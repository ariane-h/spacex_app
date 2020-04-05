<template>
  <div id="app">
    <h1>SpaceX App</h1>
    <launch-search :launches="launches"></launch-search>
    <launch-status :launches="launches"></launch-status>
    <launch-list :launches="launches"></launch-list>
    
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
import LaunchList from './components/LaunchList.vue';
import LaunchSearch from './components/LaunchSearch.vue';
import LaunchStatusFilter from '@/components/LaunchStatusFilter.vue';


export default {
  name: "app",
  components: {
    "launch-list": LaunchList,
    "launch-search": LaunchSearch,
    "launch-status": LaunchStatusFilter
  },
  data(){
    return {
      launches: [],
      searchResults: [],
      statusResults: [],
    };
  },
  methods: {
    getLaunches: function(){
      fetch("https://api.spacexdata.com/v3/launches")
      .then(res => res.json())
      .then(launches => this.launches = launches)
    },
  },
  mounted() {
    this.getLaunches();

    eventBus.$on("search-query", searchQuery => (this.searchResults = searchQuery));
    eventBus.$on("launch-status", statusFilterData => (this.statusResults = statusFilterData));
  },


};
</script>

<style>
h1{
  color:salmon;
}
</style>