<p>
  <a href="https://www.npmjs.com/package/vite-plugin-vuedoc" target="_blank">
    <img alt="Version" src="https://img.shields.io/npm/v/vite-plugin-vuedoc.svg">
  </a>
</p>

# vite-plugin-vuedoc

A markdown & vue preview plugin for vite.

## Feature

- [x] markdown component
- [x] code prism
- [x] code import
- [x] vueblock preview
- [x] vueblock sourcemap
- [x] markdown frontmatter
- [x] hmr
- [x] playground
- [ ] prism options
- [ ] tests

## Install

```sh
yarn add vite-plugin-vuedoc
```

## Options

```typescript
type VueDocPluginOptions = {
  wrapperClass: string
  previewClass: string
  markdownPlugins: any[]
}
```

- wrapperClass default: ''
  > classname wrapped markdown component
  > frontmatter `wrapperClass` will wrapped current markdown component
- previewClass default: ''
  > classname wrapped vuedemo
- markdownPlugins default: []
  > remark plugins

## Quick Start

#### use vite-plugin-vuedoc

```typescript
// vite.config.ts
import vitePluginVuedoc from 'vite-plugin-vuedoc'
const config: UserConfig = {
  plugins: [vitePluginVuedoc()]
}
export default config
```

#### style

import `vite-plugin-vuedoc/style.css` entry file

```typescript
// main.ts
import { createApp } from 'vue'
import App from './App.vue'
import 'vite-plugin-vuedoc/style.css'

const app = createApp(App)
app.mount('#app')
```

#### markdown

![markdown doc](https://github.com/JasKang/vite-plugin-vuedoc/blob/master/playground/assets/md.png?raw=true)

#### import

```typescript
import MdComp from './docs/Button.zh-CN.md'
export const router = createRouter({
  routes: [
    { path: '/home', redirect: '/' },
    {
      path: '/button',
      name: MdComp.matter.name || 'button',
      component: MdComp
    }
  ]
})
```

## VueBlock preview

If the vue block has a `demo` tag， it can preview the component

![markdown doc](https://github.com/JasKang/vite-plugin-vuedoc/blob/master/playground/assets/preview.png?raw=true)

## code import

in code block support import file like this:

\`\`\`lang file=./test.vue  
\`\`\`

## frontmatter

```
// Button.zh-CN.md
---
wrapperClass: '' // wrapperClass will wrapped current md file
title: 'title'
desc: 'desc'
---
```

```typescript
import MdComp from './docs/Button.zh-CN.md'

const { wrapperClass, title, desc } = MdComp.matter
```

## screenshots

![markdown doc](https://github.com/JasKang/vite-plugin-vuedoc/blob/master/playground/assets/vue.gif?raw=true)

> vue javascript

![markdown doc](https://github.com/JasKang/vite-plugin-vuedoc/blob/master/playground/assets/vue-js.gif?raw=true)
