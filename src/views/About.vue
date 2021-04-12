<template>
  <div class="about">
    <h1>This is an about page</h1>
  </div>
</template>

<script>

export default {
  data(){
    return{
      namepage : 'about'
    }
  },
  created(){
    this.$root.changePage(this.namepage) // this function sent namepage to root function when this page loaded 
  }
}
</script>
