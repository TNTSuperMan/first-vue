<script setup>
import {ref} from "vue";
import "./assets/style.css";
import Request from "./components/request.vue";
import Response from "./components/response.vue";
const codedatas = ref([]);
const prompt = ref("");
const place = ref(true);
function next(code){
    codedatas.value.push(code);
    place.value = undefined;
}
function clear(){
    codedatas.value = [];
    place.value = true;
}
</script>

<template>
  <h1>Hello, World!</h1>
  <p>私は今までCDNからVueを使っていたため、Viteを用いて初めてのプログラムを作りたいと思います。<br>
     サンプルとして開発するのは、開発者ツールのコンソールのような物です。</p>
  <div class="container">
    <button class="clear" @click="clear">
        クリア
    </button>
    <Response v-for="data in codedatas" :data="data" />
    <Request :code="prompt" :place="place" @entered="next"/>
  </div>  
</template>