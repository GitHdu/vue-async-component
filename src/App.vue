<template>
  <div id="app">
    <button @click="toggle">toggle</button>
    <async-component :path="path"
                     a='test'></async-component>
  </div>
</template>

<script>
import asyncComponent from './components/async-component'

export default {
  name: 'app',
  data () {
    return {
      path: 'a.vue'
    }
  },
  methods: {
    toggle () {
      this.path = 'b.vue'
    }
  },
  components: {
    asyncComponent
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
