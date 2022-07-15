<script setup>
import { nextTick, onMounted, ref } from 'vue'
// import { HighCode } from 'vue-highlight-code'
// import 'vue-highlight-code/dist/style.css'
import HighCode from './components/HighCode.vue'
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
const height = '200px'
const borderRadius = '10px'
const H = ref(null)
onMounted(() => {
  console.log(H.value.modelValue)
})
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
  margin: 20px;
}
</style>
