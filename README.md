## Highlight Code and Content editor for Vue.js

Import the npm package and only one prop to show highlightCode and editor

[![vue 3](https://img.shields.io/badge/vue-3-42b983.svg?style=flat-square)](https://vuejs.org)

<p>
  <a href="https://npm-stat.com/charts.html?package=vue-highlight-code">
    <img alt="Downloads" src="https://img.shields.io/npm/dm/vue-highlight-code.svg">
  </a>
  <a href="https://npmjs.com/package/vue-highlight-code">
    <img alt="Version" src="https://img.shields.io/npm/v/vue-highlight-code.svg"/>
  </a>
  <a href="http://packagequality.com/#?package=vue-highlight-code">
    <img alt="Quality" src="https://npm.packagequality.com/shield/vue-highlight-code.svg">
  </a>
</p>


```
yarn add highlight.js vue-highlight-code
```

## live demo
[bitSandBox-demo（web-IDE部分模块的简单实现）](https://f-one-1.github.io/bitSandBox/)  

[stackblitz](https://stackblitz.com/github/F-one-1/vue-highlight-code?file=src%2FApp.vue)

![NXGUK Z% L$P EQCLJZ6TZY](https://user-images.githubusercontent.com/68687740/169360419-e2538e66-f45e-4e5b-82d5-144f280587ca.png)

### 1. use in Vue3 

Install the `vue-highlight-code` package from NPM and `highlight.js`:

```
yarn add highlight.js vue-highlight-code
```

import the component and style

```js
import { HighCode } from 'vue-highlight-code';
import 'vue-highlight-code/dist/style.css';
export default {
    components: {
      HighCode
    },
}

<HighCode></HighCoder>
```



### Component Props

| prop            | description                                     | type      | default                                  |
| :-------------- | :---------------------------------------------- | :-------- | :--------------------------------------- |
| codeValue       | Highlight Code Source                           | `String`  | `''`                                     |
| textEditor      | CodeText Editor                                 | Boolean   | 'false'                                  |
| lang            | Highlight Code Type                             | `String`  | `javascript` (such as 'vue','html','css) |
| theme           | Component Highlight Code theme                  | `String`  | default: `dark`(only ['dark','light'])   |
| codeLines       | Show Code lines                                 | `Boolean` | `false`                                  |
| langName        | Highlight Code Name (Upper left corner display) | `String`  | ``                                       |
| width           | component style width                           | `String`  | `620px`                                  |
| height          | component style height                          | `String`  | ``                                       |
| maxWidth        | component style max-width                       | `String`  | ``                                       |
| maxHight        | component style max-height`String`              | `String`  | ``                                       |
| fontSize        | highlight code font-size                        | `Number`  | -                                        |
| scrollStyleBool | component scroll bar style                      | `Boolean` | `true`                                   |
| copy            | whether the code can copy                       | `Boolean` | `true`                                   |
| borderRadius    | component style border_radius                   | `String`  | `10px`                                   |

#### emit
| emit         | description                                                | type       | parameter                              |
| :----------- | :--------------------------------------------------------- | :--------- | :------------------------------------- |
| getCodeValue | The emit method is triggered when the edit content changes | `Function` | `function(contentValue: String): void` |


#### Get real-time editing code content

create ref  in the HighCode component instance get the modelValue 

```vue
<script setup>
const H = ref(null)
onMounted(() => {
  console.log(H.value.modelValue)
})
<script>
<HighCode ref="H" ></HighCode>

```

