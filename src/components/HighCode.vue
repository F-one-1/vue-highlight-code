<script setup>
import hljs from 'highlight.js'
import CopyCode from './CopyCode.vue'
import { computed, nextTick, ref } from 'vue'
import TypeShow from './TypeShow.vue'
const props = defineProps({
  copy: {
    type: Boolean,
    default: true,
  },
  nameShow: {
    type: Boolean,
    default: true,
  },
  langName: {
    type: String,
    // default: '',
  },
  lang: {
    type: String,
    default: 'javascript',
    requied: true,
  },
  theme: {
    type: String,
    default: 'dark',
  },
  width: {
    type: String,
    default: '620px',
  },
  height: {
    type: String,
    default: '',
  },
  maxWidth: {
    type: String,
    default: '',
  },
  maxHeight: {
    type: String,
    default: '',
  },
  scrollStyleBool: {
    type: Boolean,
    default: true,
  },
  codeValue: {
    type: String,
    requied: true,
    default: '',
  },
  fontSize: {
    type: Number,
    default: 18,
  },
  codeLines: {
    type: Boolean,
    default: false,
  },
})
const langName = props.langName || props.lang
const font_size = props.fontSize
const languageClass = 'hljs language-' + props.lang
// const theme = 'dark'
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
  // updated(el, binding) {
  //   // console.log(el, binding, '222')
  //   el.textContent = binding.value
  //   hljs.highlightElement(el)
  // },
}
const border_radius = '12px'
const withoutHeader = true

let arr = ref([])

const codeArea = ref(null)
nextTick(() => {
  const preCodeHeightDemo = codeArea.value.offsetHeight
  console.log(preCodeHeightDemo, 'preCodeHeight')
  const count = Math.floor(preCodeHeightDemo / 24)
  for (let i = 1; i <= count; i++) {
    arr.value.push(i)
  }
  // console.log(arr,'arr')
})
</script>
<template>
  <div
    class="code hljs"
    :class="{
      atom_one_dark: props.theme == 'dark',
      atom_one_light: props.theme == 'light',
    }"
    :style="{
      width: props.width,
      height: props.height,
      borderRadius: '10px',
      zIndex: '700',
      maxWidth: props.maxwidth,
      // minWidth: '540px',
      maxHeight: props.maxHeight,
      // minHeight: '240px',
    }"
  >
    <div class="code_header">
      <TypeShow v-if="nameShow" :TL="langName"></TypeShow>
      <CopyCode v-if="copy" :codeValue="props.codeValue"></CopyCode>
    </div>
    <!-- <div class="code_area">
      <div>1</div>
    </div> -->
    <div class="code_area_lines">
      <div
        :class="{
          dark: props.theme === 'dark',
          light: props.theme === 'light',
        }"
        v-for="cur in arr"
        class="code_area_lines_item"
      >
        {{ cur }}
      </div>
    </div>
    <div
      class="code_area"
      ref="codeArea"
      :style="{
        borderBottomLeftRadius: border_radius,
        borderBottomRightRadius: border_radius,
        borderTopLeftRadius: withoutHeader == true ? border_radius : 0,
        borderTopRightRadius: withoutHeader == true ? border_radius : 0,
      }"
      :class="{ srollbar_style: props.scrollStyleBool === true }"
    >
      <pre>
      <code
        v-highlight="props.codeValue"
        :class="languageClass"
        :style="{ fontSize: font_size }"
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
    padding-left: 24px;
    overflow: overlay;
    border-radius: 5px;
    display: flex;

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
    line-height: 24px;
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

.code_area_lines {
  display: flex;
  flex-direction: column;
  width: 10px;
  // justify-content: center;
  padding-top: 40px;
  align-items: center;
  position: absolute;
  transform: translateX(6px);

  &_item {
    height: 24px;
    width: 10px;
    font-size: 12px;
    color: #adb5bd;
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
    opacity: 0.6;
    &.dark {
      color: #adb5bd;
    }
    &.light {
      color: #212529;
    }
  }
}
</style>

<style>
@import '../theme/atom_one_dark.scss';
@import '../theme/atom_one_light.scss';
</style>
