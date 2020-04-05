<template lang="html">
    <div>
        <h2> Search by mission name: </h2>
        <input type="text" v-model="query" @input="sendQuery" placeholder="search launches"></input>
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
        sendQuery: function() {
        eventBus.$emit("query-input", this.query);
        },
    },
}
</script>

<style scoped>

</style>