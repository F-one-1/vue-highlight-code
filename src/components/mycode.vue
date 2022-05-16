<script setup>
import hljs from 'highlight.js'
import CopyCode from './CopyCode.vue'
import { computed } from 'vue'
import TypeShow from './TypeShow.vue'
const a = 1
let containerWidth = 100
const top = 0
const left = 0
const scrollStyleBool = true
const font_size = 18
const read_only = false
const languageClass = 'hljs language-javascript'
const value = `import CodeEditor from 'simple-code-editor111111111111111111111111111111111111111111111'
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
const htmlJs = 'JS'
const theme = 'dark'
const vHighlight = {
  bind(el, binding) {
    el.textContent = binding.value
    hljs.highlightElement(el)
  },
  componentUpdated(el, binding) {
    el.textContent = binding.value
    hljs.highlightElement(el)
  },
  created(el, binding) {
    // console.log(el, binding, '111')
    el.textContent = binding.value
    hljs.highlightElement(el)
  },
  updated(el, binding) {
    // console.log(el, binding, '222')
    el.textContent = binding.value
    hljs.highlightElement(el)
  },
}
const contentValue = computed(() => {
  return value
})

const border_radius = '12px'
const withoutHeader = true
</script>
<template>
  <div
    class="code hljs"
    :class="{
      atom_one_dark: theme == 'dark',
      atom_one_light: theme == 'light',
    }"
    :style="{
      width: '540px',
      height: '240px',
      borderRadius: '10px',
      zIndex: '600',
      maxWidth: '540px',
      minWidth: '540px',
      maxHeight: '240px',
      minHeight: '240px',
    }"
  >
    <div class="code_header">
      <TypeShow :TL="htmlJs"></TypeShow>
      <CopyCode></CopyCode>
    </div>
    <div
      class="code_area"
      :style="{
        borderBottomLeftRadius: border_radius,
        borderBottomRightRadius: border_radius,
        borderTopLeftRadius: withoutHeader == true ? border_radius : 0,
        borderTopRightRadius: withoutHeader == true ? border_radius : 0,
      }"
      :class="{ srollbar_style: scrollStyleBool === true }"
    >
      <pre
        :style="{ width: containerWidth === 0 ? '' : containerWidth + 'px' }"
      >
      <code
        v-highlight="contentValue"
        :class="languageClass"
        :style="{ top: top + 'px', left: left + 'px', fontSize: font_size, borderBottomLeftRadius: read_only == true ? border_radius : 0, borderBottomRightRadius: read_only == true ? border_radius : 0 }"
      ></code>
      </pre>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.code {
  display: flex;
  flex-direction: column;
  font-size: 0;
  position: relative;
  text-align: left;
  overflow: hidden;
  &_area {
    position: relative;
    overflow: hidden;
    padding: 20px;
    padding-top: 0px;
    overflow: overlay;
    border-radius: 5px;
    &.srollbar_style::-webkit-scrollbar-track {
      background-color: #eee;
      // border-radius: 5px;
    }
    &.srollbar_style::-webkit-scrollbar-thumb {
      background: rgb(175, 171, 171);
      // border-radius: 5px;
    }
    &.srollbar_style::-webkit-scrollbar {
      width: 8px;
      height: 8px;
    }
    &.srollbar_style::-webkit-scrollbar-corner {
      background-color: #eee;
    }
  }
  &_header {
    position: relative;
    display: flex;
    justify-content: space-around;
    height: 40px;
    width: 100%;
  }
  pre code {
    // padding: 0px 20px 20px 20px;
    font-family: Consolas, Monaco, monospace;
    line-height: 1.5;
    font-size: 16px;
  }
}
.wrapper-content::-webkit-scrollbar-track {
  background-color: #eee;
  border-radius: 5px;
}
.wrapper-content::-webkit-scrollbar-thumb {
  background: rgb(175, 171, 171);
  border-radius: 5px;
}
.wrapper-content::-webkit-scrollbar {
  width: 6px;
}
</style>

<style>
@import '../theme/atom_one_dark.scss';
@import '../theme/atom_one_light.scss';
</style>
