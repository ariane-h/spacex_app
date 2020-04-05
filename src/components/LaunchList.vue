<template lang="html">
  <div class="launch-list">
      <div class="launch-list-title"><h2>Launch List</h2></div>
      <div class="launch-list-items">
          <launch-list-item
            v-for="(launch, index) in launches"
            :launch="launch"
            :key="index">
            </launch-list-item>
      </div>
  </div>
</template>

<script>
import LaunchListItem from "@/components/LaunchListItem.vue";

export default {
    name: "launch-list",
    props: ["launches"],
    components: {
        "launch-list-item": LaunchListItem
    }

}
</script>

<style scoped>
.launch-list{
    padding-left: 23%;
}
.launch-list-items{
    height: 450px;
    overflow-x: scroll;
}
</style>