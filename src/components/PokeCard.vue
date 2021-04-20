<template>
  <div>
    <poke-search @poke-name="getPokename"></poke-search>
  </div>
  <div class="flex flex-wrap -mx-4">
    <div v-for="poke in filterPoke" :key="poke.id" class="md:w-1/3 px-1 mb-9">
      <div class="flex flex-col items-center">
        <img :src="poke.pokemonImg" alt="image" class="w-36"/>
        <p>{{ poke.pokemonName }}</p>
      </div>
    
    </div>
  </div>
</template>

<script>
import PokeSearch from "./PokeSearch.vue";
export default {
  components: { PokeSearch },
  data() {
    return {
      pokedex: [],
      pokename: "",
    };
  },
  methods: {
    async getPokeData() {
      try {
        const res = await fetch(this.$root.dburl);
        const data = await res.json();
        return data;
      } catch (error) {
        console.log(`error: ${error}`);
      }
    },
    getPokename(value) {
      this.pokename = value;
    },
  },
  computed: {
    filterPoke() {
      return this.pokedex.filter((poke) => {
        return poke.pokemonName
          .toLowerCase()
          .includes(this.pokename.toLowerCase()); // filter by name object, if searchText contained in object it reture ture
      });
    },
  },
  async created() {
    this.pokedex = await this.getPokeData();
  },
};
</script>
