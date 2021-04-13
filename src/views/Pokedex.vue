<template>
  <div>
    <RegisForm/>
  </div>
</template>

<script>
import RegisForm from "../components/RegisForm.vue";
export default {
  components: {
    RegisForm
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
