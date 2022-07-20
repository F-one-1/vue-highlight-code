<script setup>
import { nextTick, onMounted, ref } from 'vue'
// import HighCode from 'vue-highlight-code'
// import 'vue-highlight-code/dist/style.css'
import HighCode from './components/HighCode.vue'
// import { HighCode } from 'vue-highlight-code'
// import 'vue-highlight-code/dist/style.css'
const value = `body {
  padding: 0;
  margin: 0;
}
.App {
  text-align: center;
}
.App-header {
  background-color: #282c34;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: calc(10px + 2vmin);
  color: white;
}
.App-link {
  color: #61dafb;
}
button {
  font-size: calc(10px + 2vmin);
}`
const light = 'light'
const vue = 'vue'
const dark = 'dark'
const height = '200px'
const borderRadius = '10px'
const H = ref(null)
onMounted(() => {
  console.log(H.value.modelValue)
})
const getCodeValue = (v) => {
  console.log(v)
}
</script>
<template>
  <div class="wrapper">
    <div ref="d"></div>
    <HighCode ref="H" class="code" :codeValue="value" :theme="dark"></HighCode>
    <HighCode
      ref="High"
      class="code"
      :codeValue="value"
      :theme="light"
      :borderRadius="borderRadius"
      :nameShow="false"
      :copy="false"
      :textEditor="true"
      @getCodeValue="getCodeValue"
    ></HighCode>
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
  /* margin: 20px; */
}
</style>
