<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <div><Module msg="This is a module"/></div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import Module from '@/components/Module.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld,
    Module
  }
}
</script>
