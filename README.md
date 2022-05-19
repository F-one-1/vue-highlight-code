## Highlight Code for Vue.js

Import the npm package and only one prop to show highlightCode

```
yarn add highlight.js vue-highlight-code
```
## live demo

[stackblitz](https://stackblitz.com/edit/github-flf8ku?file=README.md)

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



### 2. Props

#### codeValue `String`

Description:  Highlight Code



#### lang `String`

default: 'javascript'    (such as 'vue','html','css')

Description: Highlight Code Type



#### theme `String`

default: 'dark'     (only ['dark','light'])

Description: Highlight Code theme

#### codeLines `Boolean`

default： false

Description:  Support Code lines

#### langName `String`

Description: Highlight Code Name (Upper left corner display)

 

#### width `String`

default: '620px'

Description: the component width



#### height `String`

Description: the component height



#### maxWidth `String`

Description: the component max-width



#### maxHeight `String`

Description: the component max-height



#### fontSize `Number`

Description: the highlight code font-size



#### scrollStyleBool `Boolean`

default: true

Description:  scroll bar style 



#### copy `Boolean`

default： true

Description:  whether the code can copy

