

# go

```
npm install -g vue-cli
vue init webpack vuedemo
cd vuedemo
npm install
npm install element-ui --save


```

* 修改main.js
```
import Vue from 'vue'
import App from './App'
import router from './router'

import { Button, Select } from 'element-ui'
import 'element-ui/lib/theme-chalk/index.css'

Vue.config.productionTip = false


Vue.use(Button)
Vue.use(Select)

/* eslint-disable no-new */

new Vue({
  el: '#app',
  router,
  template: '<App/>',
  components: { App }
})
```
* 修改App.vue
```
<template>
  <div id="app">
    <img src="./assets/logo.png">
    <el-button>默认按钮</el-button>
    <router-view></router-view>
  </div>
</template>

```
* npm run dev


