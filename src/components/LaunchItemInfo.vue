<template>
  <div class="main-info-container">
      <div id="info-text-container">
        <h2>{{ launch.mission_name }}</h2>

        <p>Year: {{ launch.launch_year }}</p>

        <p v-show="launch.launch_success">Launch Status: Success</p>
        <p v-show="!launch.launch_success">Launch Status: Failure </p>

        <p>Rocket: {{ launch.rocket.rocket_name }}</p>
        <p>Launch Site: {{ launch.launch_site.site_name_long }}</p>
        
        <p>Details: {{ launch.details }}</p> 

        <p>Payload(s):</p>
        <ul >
            <li v-for="(payload, index) in launch.rocket.second_stage.payloads" :payload="payload" :key="index"> {{ payload.payload_type }} for  {{ payload.nationality }}</li>
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

img{
    margin-right: 16%;
    margin-left: 16%;
    margin-top: 5%;
}



</style>