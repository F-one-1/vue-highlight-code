<script setup>
import { nextTick, onMounted, ref } from 'vue'
// import HighCode from 'vue-highlight-code'
// import 'vue-highlight-code/dist/style.css'
import HighCode from './components/HighCode.vue'
// import { HighCode } from 'vue-highlight-code'
// import 'vue-highlight-code/dist/style.css'
const value = `import { HighCode } from 'vue-highlight-code';
import 'vue-highlight-code/dist/style.css';
export default {
    components: {
      HighCode
    },
    data(){

    }
}`
const value2 = `#app {
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
`
const light = 'light'
const vue = 'vue'
const dark = 'dark'
const borderRadius = '10px'
const fontSize = '12px'
const height = '60px'
const width = '580px'
const H = ref(null)
onMounted(() => {
  console.log(H.value.modelValue)
})
const getCodeValue = (v) => {
  console.log(v)
}
const booltrue = true
const boolfalse = false
</script>
<template>
  <div class="wrapper">
    <div ref="d"></div>
    <HighCode
      ref="H"
      class="code"
      :codeValue="value"
      :theme="dark"
      :fontSize="fontSize"
      :nameShow="false"
      :copy="true"
      :height="height"
      :width="width"
      :textEditor="true"
    ></HighCode>
    <HighCode
      ref="H"
      class="code"
      :codeValue="value2"
      :theme="dark"
      :fontSize="fontSize"
      :nameShow="false"
      :copy="false"
      :height="height"
      :width="width"
      :readOnly="boolfalse"
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
