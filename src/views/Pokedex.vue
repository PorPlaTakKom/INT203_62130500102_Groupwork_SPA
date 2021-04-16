<template>
  <div class="bg-red-600 rounded-md m-5 p-5 shadow-xl">
    <RegisForm/>
  </div>
  <div>
    <PokeTable/>
  </div>
</template>

<script>
import RegisForm from "../components/RegisForm.vue";
import PokeTable from "../components/PokeTable.vue";
export default {
  components: {
    RegisForm,
    PokeTable
  },
  data() {
    return {
      namepage: "pokedex",
    }
  },
  created() {
    this.$root.changePage(this.namepage); // this function sent namepage to root function when this page loaded
  }
};
</script>
