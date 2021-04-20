<template>
  <input placeholder="pokename" :value="pokename" @input="demo($event.target.value)" class="p-1 rounded-md w-5/12 focus:outline-none"> 
</template>

<script>
export default {
  props:{
    pokename:{
      type: String,
      default: 'Pikachu'
    }
  },
  methods:{
      demo(value){
        this.$emit('poke-name',value)
      }
  }
}
</script>
