<template>
  <div id="app">
    <h1>SpaceX App</h1>
    <launch-list :launches="launches"></launch-list>
  </div>
</template>

<script>
import LaunchList from './components/LaunchList.vue';


export default {
  name: "app",
  components: {
    "launch-list": LaunchList,
  },
  data(){
    return {
      launches: [],
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
  }


};
</script>

<style>
h1{
  color:salmon;
}
</style>