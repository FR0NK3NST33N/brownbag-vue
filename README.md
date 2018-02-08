# brownbag-vue

> A Vue.js project

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm test
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

# Setup

- built project with `vue init webpack <project_name>`

- `npm run dev` launches on localhost:8080

- we need to first make some edits to our router config in order to route without a change to our url

- modify `router/index.js`
```
import Vue from 'vue'
import Router from 'vue-router'
import HelloWorld from '@/components/HelloWorld'

Vue.use(Router)

export default new Router({
  routes: [
    {
      path: '/',
      name: 'HelloWorld',
      component: HelloWorld
    }
  ],
  mode: 'abstract'
})
```

- we added the `mode: 'abstract'` to our router defenition

- modify `main.js`
```
import Vue from 'vue'
import App from './App'
import router from './router'

Vue.config.productionTip = false

/* eslint-disable no-new */
new Vue({
  el: '#app',
  router,
  components: { App },
  template: '<App/>'
})

router.replace('/')
```

- we added the `router.replace('/')`

- We can then duplicate our HelloWorld component to make a new Test component
- Move our HelloWorld and Test Components toa new folder called views
- Change the name of our component
- Add the route to our new component and their new locations
```
import Vue from 'vue'
import Router from 'vue-router'
import HelloWorld from '@/views/HelloWorld'
import Test from '@/views/Test'

Vue.use(Router)

export default new Router({
  routes: [
    {
      path: '/',
      name: 'HelloWorld',
      component: HelloWorld
    },
    {
      path: '/test',
      name: 'Test',
      component: Test
    }
  ],
  mode: 'abstract'
})
```

- final views should look something like:
```
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <router-link to="/">Go to Home</router-link>
  </div>
</template>

<script>
export default {
  name: 'Test',
  data () {
    return {
      msg: 'Welcome to the Test Page of Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  font-weight: normal;
}
</style>
```

- create links to views on both the HelloWorld and Test Component
```
<router-link to="/test">Go to Test</router-link>
<router-link to="/">Go to Home</router-link>
```

- Lets create a global component Nav
- copy a view to `components/` and rename it `Nav.vue`
```
<template>
  <div>
    <router-link to="/"><button>Go to Home</button></router-link>
    <router-link to="/test"><button>Go to Test</button></router-link>
    <br />
    <br />
  </div>
</template>

<script>
export default {
  name: 'Nav',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
a {
  float: left;
}
</style>
```

- so now lets import our nav component into our app component so we can have it persist the route changes
```
<template>
  <div id="app">
    <sijl-nav></sijl-nav>
    <img src="./assets/logo.png">
    <router-view/>
  </div>
</template>

<script>
import Nav from '@/components/Nav'

export default {
  name: 'App',
  components: {
    'sijl-nav': Nav
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
```



