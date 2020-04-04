<template>
  <div id="app">
    <h1>SpaceX App</h1>
    <launch-search :searchQuery="searchQuery"></launch-search>
    <launch-list :launches="launches"></launch-list>
  </div>
</template>

<script>
import { eventBus } from "@/main.js";
import LaunchList from './components/LaunchList.vue';
import LaunchSearch from './components/LaunchSearch.vue';


export default {
  name: "app",
  components: {
    "launch-list": LaunchList,
    "launch-search": LaunchSearch
  },

  data(){
    return {
      launches: [],
      searchQuery: ""
    };
  },

  methods: {
    getLaunches: function(){
      fetch("https://api.spacexdata.com/v3/launches")
      .then(res => res.json())
      .then(launches => this.launches = launches)
    }

  },
  mounted() {
    this.getLaunches();

    eventBus.$on("query-input", query => (this.searchQuery = query));
  }


};
</script>

<style>
h1{
  color:salmon;
}
</style>