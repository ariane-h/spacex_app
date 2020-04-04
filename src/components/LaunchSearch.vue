<template lang="html">
    <div>
        <h2> search the launches: </h2>
        <input type="text" v-model="query" @input="sendQuery(query)" placeholder="search launches"></input>
    </div>
</template>

<script>

import { eventBus } from "@/main.js";

export default {
    name: "launch-search",
    data(){
        return{
            query: ""
        };
    },
    methods: {
        sendQuery: function(query) {
        eventBus.$emit("query-input", query);
        },
    },
}
</script>

<style>

</style>