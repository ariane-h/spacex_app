<template lang="html">
    <div>
        <h2> Search by mission name: </h2>
        <input type="text" v-model="searchQuery" @input="sendQuery" placeholder="search launches"></input>
    </div>
</template>

<script>

import { eventBus } from "@/main.js";

export default {
    name: "launch-search",
    props: ["launches"],
    data(){
        return{
            searchQuery: ""
        };
    },
    computed: {
        searchResults: function(){
            return this.launches.filter((launch) => {
                return launch.mission_name.toLowerCase().match(this.searchQuery.toLowerCase());
            })
        }
    },
    methods: {
        sendQuery: function() {
        eventBus.$emit("search-query", this.searchResults);
        },
    },
};
</script>

<style>

</style>