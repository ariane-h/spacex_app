<template lang="html">
  <div class="launch-list">
      <h2>Launch List</h2>
      <launch-list-item
      v-for="(launch, index) in launches"
      :launch="launch"
      :key="index">
      </launch-list-item>
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

</style>