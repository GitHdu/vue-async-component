<template>
  <div id="app">
    <li v-for="i in arr">{{i.name}}</li>
    <button @click="toggle">toggle</button>
    <!-- <async-component :path="path"
                     a='test'></async-component> -->
    <!-- <ab v-if="test"></ab> -->
  </div>
</template>

<script>
import asyncComponent from './components/async-component'
function loadView (view) {
  return () => import(/* webpackChunkName: "view-[request]" */ `@/views/${view}.vue`)
}
export default {
  name: 'app',
  data () {
    return {
      path: 'a.vue',
      arr: [{ id: 'a', name: '1' }, { id: 'b', name: 2 }],
      test: false
    }
  },
  methods: {
    toggle () {
      this.arr.splice(1, 1, { id: 'c', name: 3 })
      // this.path = 'b.vue'
      // this.test = true
    }
  },
  computed: {
    a () {
      this.arr[0].checked = true
    }
  },
  components: {
    asyncComponent,
    ab: loadView('b')
  },
  created () {
    console.log(this._self)
  }
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
