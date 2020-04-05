<template lang="html">
    <div id="search-query">
        <div><h2> Search by mission name: </h2></div>
        <div class="search-box"><input type="text" v-model="query" @input="sendQuery" placeholder="search launches"></input></div>
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
#search-query{
    display:flex;
    justify-content: center;
    margin: 1%;
}

.search-box{
    align-self: center;
    padding-left: 10px;
}

.search-box, input{
    font-size: 15px;
}

</style>