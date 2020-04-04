<template>
  <div>
      <p>{{ launch.mission_name }}</p>
  </div>
</template>

<script>


export default {
    name: "launch-list-item",
    props: ["launch"],
};
</script>

<style>

</style>