<template>
  <div>
    this is a
    {{arr}}
  </div>
</template>

<script>
export default {
  props: ['a'],
  data () {
    return {
      arr: [1]
    }
  },
  computed: {
    t () {
      return this.arr
    }
  },
  created () {
    setTimeout(() => {
      this.arr = Object.freeze([1, { a: 3 }])
      this.$nextTick(() => {
        console.log(this.t)
      })
    }, 1000)
    console.log(this.a)
  }
}
</script>

<style scoped>
</style>
