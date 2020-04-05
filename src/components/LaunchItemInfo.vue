<template>
  <div>
      <h1>launch item info</h1>
      <p>{{ launch.mission_name }}</p>
      <p>other launch details here</p>
  </div>
</template>

<script>


export default {
    name: "launch-item-info",
    props: ['launch'],
}
</script>

<style scoped>

</style>