<template>
  <component v-bind:is="AsyncComponent"
             v-bind="$attrs"
             v-on="$listeners"></component>
</template>

<script>
export default {
  props: {
    path: {
      type: String,
      required: true,
      default: () => null
    }
  },
  data () {
    // console.log(this.render)
    // const AsyncComponent = this.render
    return {
      AsyncComponent: ''
    }
  },
  methods: {
    render () {
      this.AsyncComponent = () => ({
        component: import(`@/views/${this.path}`),
        loading: { render () {
          return '<div style="height: 100%; width: 100%; display: table;"><div style="display: table-cell; vertical-align: middle; text-align: center;"><div>加载中</div></div></div>'
        } },
        error: { template: '<div style="height: 100%; width: 100%; display: table;"><div style="display: table-cell; vertical-align: middle; text-align: center;"><div>加载错误</div></div></div>' },
        delay: 200,
        timeout: 10000
      })
    }
  },
  watch: {
    path: {
      handler () {
        this.render()
      },
      immediate: true
    }
  }
}
</script>
