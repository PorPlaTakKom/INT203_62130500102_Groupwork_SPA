<template>
    <base-card class="bg-yellow-300">
      <div class="text-white text-3xl font-bold">
        <img class="w-1/6 mx-auto" alt="logo" src="../images/pikachu.png" />
        <p>Welcome</p>
        <p class="text-2xl">This site is a collection of Pokemon's information</p>
      </div>
    </base-card>
    <base-card class="bg-yellow-200">
      <PokeCard/>
    </base-card>
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
