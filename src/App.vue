<template>
  <div id="app">
    <div id="title"><h1>SpaceX Launches</h1></div>
    <launch-search :searchQuery="searchQuery" ></launch-search>

    <div id="launch-container">
     
        <launch-list :launches="filteredLaunches"></launch-list>
    

     
        <launch-item-info
            v-if="selectedLaunch"
            :launch="selectedLaunch">
        </launch-item-info>
   
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

#app{
  padding: 1%;
}

#title{
  display:flex;
  justify-content: center;
}

#launch-container{
  display: grid;
  grid-template-columns: 40% auto;
}
</style>