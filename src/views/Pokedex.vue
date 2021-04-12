<template>
  <div>
    <p>Hello World</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      namepage: 'pokedex',
    }
  },
  created() {
    this.$root.changePage(this.namepage); // this function sent namepage to root function when this page loaded 
  },
};
</script>
