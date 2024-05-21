<script setup>
import Request from "./request.vue";
const props = defineProps(["data"]);
const data = props.data;
let result;
try{
    result = eval(data);
    console.log(result);
    if(result === undefined){
        result = "undefined";
    }
    if(result === null){
        result = "null";
    }
    if(typeof(result) == "object"){
        result = JSON.stringify(result);
    }
}
catch(e){
    result = e;
}
</script>
<template>
    <Request :code="data" readonly/>
    <div class="result">{{ result }}</div>
</template>
<style>
.result{
    background:#aaa;
    display:inline-block;
}
.result::before{
    content:"> ";
    color:gray;
}
</style>