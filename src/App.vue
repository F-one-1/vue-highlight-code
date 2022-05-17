<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from './components/HelloWorld.vue'
import {HighCode} from 'vue-highlight-code'
import 'vue-highlight-code/dist/style.css'
const value = `import CodeEditor from 'simple-code-editor'
export default {
    components: {
      CodeEditor
    },
    data() {
        return {
          value: ''
        }
    }
}`
const light = 'light'
</script>
<template>
  <div class="wrapper">
    <HighCode class="code" :codeValue="value" :theme="dark"></HighCode>
    <HighCode class="code" :codeValue="value" :theme="light"></HighCode>
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
