<template>
    <div class="h-auto w-auto m-5 p-3 bg-yellow-300 rounded-md shadow-xl">
      <div class="text-white text-3xl font-bold">
        <img class="w-1/6 mx-auto" alt="logo" src="../images/pikachu.png" />
        <p>Welcome</p>
        <p class="text-2xl">This site is a collection of Pokemon's information</p>
      </div>
    </div>
    <div class="h-auto w-auto m-5 p-5 bg-yellow-200 rounded-md shadow-xl">
      <PokeCard/>
    </div>
</template>

<script>
import PokeCard from "../components/PokeCard.vue";
export default {
  components:{
    PokeCard
  },
  data() {
    return {
      namepage: "home",
      pokename: {}
    }
  },
  methods: {
  },
  created() {
    this.$root.changePage(this.namepage); // this function sent namepage to root function when this page loaded
  },
};
</script>
