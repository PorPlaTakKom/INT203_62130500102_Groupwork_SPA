<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  data(){
    return{
      namepage : 'home'
    }
  },
  name: 'Home',
  created(){
    this.$root.changePage(this.namepage)
  },
  components: {
    HelloWorld
  }
}
</script>
