<template>
  <div class="flex flex-col">
    <div class="-my-2 overflow-x-auto">
      <div class="py-2 align-middle inline-block min-w-full">
        <div
          class="shadow overflow-hidden border-b border-gray-200 sm:rounded-lg">
          <table class="w-full divide-y divide-gray-200">
            <thead class="bg-red-600 rounded-t-xl">
              <tr>
                <th class="px-6 py-3 text-white uppercase">Pokemon Name</th>
                <th class="px-6 py-3 text-white uppercase">Height</th>
                <th class="px-6 py-3 text-white uppercase">Weight</th>
                <th class="px-6 py-3 text-white uppercase">Type</th>
                <th class="relative px-6 py-3">
                  <span class="sr-only">Edit</span>
                </th>
              </tr>
            </thead>
            <tbody class="bg-white">
              <tr v-for="poke in pokedex" :key="poke.id">
                <td class="px-3 py-4 whitespace-nowrap">
                  <div class="flex flex-col items-center">
                    <img class="f h-10 w-10 rounded-full " v-bind:src="poke.pokemonImg" alt="poke-image">
                    <div class="text-sm font-medium text-gray-900">
                    {{ poke.pokemonName }}
                    </div>
                  </div>
                </td>
                <td class="px-6 py-4 whitespace-nowrap">
                  <div class="text-sm text-gray-900">
                    {{ poke.pokemonHeight }}
                  </div>
                </td>
                <td class="px-6 py-4 whitespace-nowrap">
                  <div class="text-sm text-gray-900">
                    {{ poke.pokemonWeight }}
                  </div>
                </td>
                <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-500">
                  {{ poke.pokemonType }}
                </td>
                <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">
                  <a href="#" class="text-indigo-600 hover:text-indigo-900">Edit</a>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PokeTable",
  data() {
    return {
      pokedex: [],
    };
  },
  methods: {
    async getPokeData() {
      try {
        const res = await fetch("http://localhost:5000/pokedex");
        const data = await res.json();
        return data;
      } catch (error) {
        console.log(`error: ${error}`);
      }
    },
  },
  async created() {
    this.pokedex = await this.getPokeData();
  },
};
</script>