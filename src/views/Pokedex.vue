<template>
  <base-card class="bg-red-600">
    <RegisForm/>
  </base-card>
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
