<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from './components/HelloWorld.vue'
import {HighCode} from 'vue-highlight-code'
import 'vue-highlight-code/dist/style.css'
const value = `import { HighCode } from 'vue-highlight-code';
import 'vue-highlight-code/dist/style.css';
export default {
    components: {
      HighCode
    },
    data(){
      
    }
}`
const light = 'light'
const vue = 'vue'
const dark = 'dark'
</script>
<template>
  <div class="wrapper">
    <HighCode class="code" :codeValue="value" :theme="dark" :lang="vue"></HighCode>
    <HighCode class="code" :codeValue="value" :theme="light" :lang="vue"></HighCode>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.wrapper {
  display: flex;
  flex-direction: column;
}
.code {
  margin: 20px;
}
</style>
