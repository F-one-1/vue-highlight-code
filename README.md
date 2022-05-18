## Highlight Code for Vue.js

Import the npm package and only one prop to show highlightCode


## live demo

[stackblitz](https://stackblitz.com/edit/github-flf8ku?file=README.md)


### 1. use in Vue3 

Install the `vue-highlight-code` package from NPM:

```
yarn add vue-highlight-code
```

import the component and style

```vue
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

