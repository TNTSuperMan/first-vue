<script setup>
import {ref} from "vue";
const emit = defineEmits(["entered"]);
const props= defineProps(["readonly", "code", "place"])
const isReadonly = props.readonly;
const code = ref(props.code);
const place = props.place ? 
    "Input Javascript code..." : undefined;
function Input(e){
    if(e.code == "Enter"){
        emit("entered", code.value);
        code.value = "";
    }
}
</script>
<template>
    <input class="request" type="text" name="request" :readonly="isReadonly"
    @keydown="Input" v-model="code" :placeholder="place">
</template>
<style>
.request{
    background:skyblue;
    border: none;
}
</style>