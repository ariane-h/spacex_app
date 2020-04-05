<template>
  <div class="main-info-container">
      <div id="info-text-container">
        <h1>launch item info</h1>
        <h2>Mission Name: {{ launch.mission_name }}</h2>
        <p>Year: {{ launch.launch_year }}</p>
        <p>Launch Site: {{ launch.launch_site.site_name_long }}</p>
        <p>Rocket: {{ launch.rocket.rocket_name }}</p>

        <p v-show="launch.launch_success">Launch Status: Success</p>
        <p v-show="!launch.launch_success">Launch Status: Failure </p>
        
        <p> Details: {{ launch.details }}</p> 

        <p>Payloads:</p>
        <ul >
            <li v-for="(payload, index) in launch.rocket.second_stage.payloads" :payload="payloads" :key="index">Type: {{ payload.payload_type }}, Customer: {{ payload.nationality }}</li>
            </ul>
        </div>

        <div id="image-container">
            <img :src="launch.links.mission_patch_small">
        </div>
  </div>
</template>

<script>


export default {
    name: "launch-item-info",
    props: ['launch'],
}
</script>

<style scoped>
.main-info-container{
    display: grid;
    grid-template-columns: 50% 50%;
}

</style>