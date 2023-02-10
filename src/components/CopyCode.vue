<script setup>
import { ref } from 'vue'
let Tips = ref('copy ?')
let text = ref('copy')
const resetMessage = () => {
  text.value = 'copy'
}
const props = defineProps({
  codeValue: {
    type: String,
    default: 'console.log(',
    required: true,
  },
})
const copy = (event) => {
  getContent()
  event.target.focus()
  text.value = 'copied'
}
const textarea = ref(null)
const getContent = () => {
  let textArea = textarea.value
  console.log(textArea, 'textArea')
  if (document.execCommand('copy') == true) {
    console.log('document.execCommandtrue')
    // older browser support
    let range, selection
    textArea.focus()
    textArea.select()
    range = document.createRange()
    range.selectNodeContents(textArea)
    console.log(range, 'range')
    selection = window.getSelection()
    selection.removeAllRanges()
    selection.addRange(range)
    textArea.setSelectionRange(0, textArea.value.length)
    document.execCommand('copy')
  } else {
    // modern browser support (using the clipboard API)
    console.log('navigator.clipboard.writeText(textArea.value)')
    navigator.clipboard.writeText(props.codeValue)
  }
}
</script>

<template>
  <!-- <input type="text" /> -->
  <div class="cb" tabindex="0" @focusout="resetMessage" @click="copy">
    <!-- <div class="cb_tooltip">{{ Tips }}</div> -->
    <textarea
      ref="textarea"
      :value="props.codeValue"
      tabindex="1"
      readonly
    ></textarea>
    <div class="cb_copy">{{ text }}</div>
    <!-- <div v-show='copyjudge' class="cb_copy">copied</div> -->
  </div>
</template>

<style lang="scss">
.cb {
  // display: flex;
  position: absolute;
  cursor: pointer;
  transition: 0.3s opacity linear;
  opacity: 0.5;
  height: 30px;
  width: 80px;
  // float: right;
  top: 0px;
  right: 0px;
  // justify-content: flex-end;
  &:hover &_tooltip {
    display: block;
  }
  &:hover {
    opacity: 1;
  }
  &_tooltip {
    font-family: sans-serif;
    display: none;
    position: absolute;
    // bottom: -10px;
    left: -96px;
    font-size: 12px;
    color: white;
    width: 80px;
    height: 30px;
    line-height: 30px;
    background: rgba(0, 0, 0, 0.8);
    box-sizing: border-box;
    text-align: center;
    border-radius: 4px;
  }
  &_copy {
    position: absolute;
    font-family: sans-serif;
    // display: none;
    // position: relative;
    display: block;
    // float: right;
    // display: flex;
    // justify-content: flex-end;
    // bottom: -10px;
    // left: -96px;
    font-size: 12px;
    color: white;
    // right: 0px;
    width: 80px;
    height: 30px;
    line-height: 30px;
    background: rgba(0, 0, 0, 0.8);
    box-sizing: border-box;
    text-align: center;
    border-radius: 4px;
  }
  textarea {
    user-select: none;
    position: absolute;
    padding: 0;
    width: 0;
    height: 0;
    background: transparent;
    resize: none;
    opacity: 0;
    border-color: rgba(0, 0, 0, 0);
  }
}
</style>
