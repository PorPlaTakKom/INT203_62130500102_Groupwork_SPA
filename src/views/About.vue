<template>
  <base-card class="bg-blue-500 text-white">
    <h1 class="font-bold text-xl">About Page</h1>
    <p>
      This website for INT203, It develop by vue cli and tailwindcss 
    </p>
  </base-card>
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
