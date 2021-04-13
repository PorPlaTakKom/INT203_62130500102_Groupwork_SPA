<template>
  <div>
    <img class="w-1/6 mx-auto" alt="logo" src="../images/pikachu.png" />
    <div class="text-white text-3xl font-bold">
      <p>Welcome</p>
      <p class="text-2xl">This site is a collection of Pokemon's information</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      namepage: "home",
    };
  },
  methods: {},
  created() {
    this.$root.changePage(this.namepage); // this function sent namepage to root function when this page loaded
  },
};
</script>
