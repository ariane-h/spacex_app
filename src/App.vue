<template>
  <div id="app">
    <h1>SpaceX App</h1>
    <launch-search :searchQuery="searchQuery" ></launch-search>

    <div id="launch-container">
      <div id="launch-list">
        <launch-list :launches="filteredLaunches"></launch-list>
      </div>

      <div id="launch-info">
        <launch-item-info
            v-if="selectedLaunch"
            :launch="selectedLaunch">
        </launch-item-info>
      </div>
    </div>

  </div>
</template>

<script>
import { eventBus } from "@/main.js";
import LaunchList from './components/LaunchList.vue';
import LaunchSearch from './components/LaunchSearch.vue';
import LaunchItemInfo from './components/LaunchItemInfo.vue';


export default {
  name: "app",
  components: {
    "launch-list": LaunchList,
    "launch-search": LaunchSearch,
    "launch-item-info": LaunchItemInfo 
  },

  data(){
    return {
      launches: [],
      searchQuery: "",
      selectedLaunch: null,
    };
  },
  computed: {
    filteredLaunches: function(){
      return this.launches.filter((launch) => {
        return launch.mission_name.toLowerCase().match(this.searchQuery.toLowerCase());
      })
    }
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

    eventBus.$on("query-input", query => (this.searchQuery = query));
    eventBus.$on("launch-selected", launch => (this.selectedLaunch = launch));
  }


};
</script>

<style>
h1{
  color:salmon;
}

#launch-container{
  display: grid;
  grid-template-columns: auto auto;
}
</style>