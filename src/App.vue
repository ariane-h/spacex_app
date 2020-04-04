<template>
  <div id="app">
    <h1>SpaceX App</h1>
  </div>
</template>

<script>
export default {
  name: "app",
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