<template>
  <div id="app">
    <button @click="test">Toast</button>
  </div>
</template>

<script>
import Toast from './components/Toast.vue';
import Vue from 'vue'

export default {
  name: 'app',
  created() {
    // console.log(this.$toast)
  },
  methods: {
    test() {
      this.toast('Hello')
    },
    toast(msg, options = {}) {
      options.message = msg
      let toast = Vue.extend(Toast)
      console.log(toast)
      if (!toast.$el) {
        let vm = toast.$mount()
        document.querySelector(options.parent || 'body').appendChild(vm.$el)
      }
      toast.queue.push(options)
    }
  }
};
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
