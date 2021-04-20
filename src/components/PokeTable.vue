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
              <tr v-for="poke in pokedex" :key="poke.id" v-show="!isEdit">
                <td class="px-3 py-4 whitespace-nowrap" >
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
                  <a href="#" @click="showEdit(poke)" class="text-indigo-600">Edit</a>
                  <a href="#" @click="removePoke(poke.id)" class="text-red-600 pl-5">Delete</a>
                </td>
              </tr>

              <tr v-show="isEdit">
                  <td class="px-3 py-4 whitespace-nowrap " >
                      <div class="text-sm font-medium text-gray-900">
                        <input class="p-1 border-red-400 border-2 focus:outline-none rounded-md text-center" v-model="editpokedex.pokemonName">
                      </div>
                  </td>
                  <td class="px-6 py-4 whitespace-nowrap">
                    <div class="text-sm text-gray-900">
                      <input class="p-1 w-6/12 border-red-400 border-2 focus:outline-none rounded-md text-center" v-model="editpokedex.pokemonHeight">
                    </div>
                  </td>
                  <td class="px-6 py-4 whitespace-nowrap">
                    <div class="text-sm text-gray-900">
                      <input class="p-1 w-6/12 border-red-400 border-2 focus:outline-none rounded-md text-center" v-model="editpokedex.pokemonWeight">
                    </div>
                  </td>
                  <td class="px-6 py-4 whitespace-nowrap text-sm text-gray-900">
                    <input class="p-1 w-9/12 border-red-400 border-2 focus:outline-none rounded-md text-center" v-model="editpokedex.pokemonType">
                  </td>
                  <td class="px-6 py-4 whitespace-nowrap text-right text-sm font-medium">
                    <a href="#" @click="editPoke(this.editpokedex)" class="text-indigo-600">Submit</a>
                    <a href="#" @click="canceledit" class="text-red-600 pl-5">Cancel</a>
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
      isEdit: false,
      pokedex: [],
      editpokedex: {}
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
    async removePoke(id){
      try{
        await fetch(`http://localhost:5000/pokedex/${id}`, {
          method: 'DELETE'
        })
        this.pokedex = await this.getPokeData()
        console.log('Remove Successful')
      }catch(e){
        console.log(`Error: ${e}`)
      }
    },
    showEdit(poke){
      this.editpokedex = poke
      this.isEdit = !this.isEdit
    },
    async canceledit(){
      this.isEdit = !this.isEdit
      this.editpokedex = {}
      this.pokedex = await this.getPokeData()
      console.log('Cancel Edit!!')
    },
    async editPoke(newPoke){
      try{
        const res = await fetch(`http://localhost:5000/pokedex/${newPoke.id}`,{
          method: 'PUT',
          headers:{
            'content-type': 'application/json'
          },
          body:JSON.stringify({
            pokemonName: newPoke.pokemonName,
            pokemonHeight: newPoke.pokemonHeight,
            pokemonWeight: newPoke.pokemonWeight,
            pokemonType: newPoke.pokemonType,
            pokemonImg: newPoke.pokemonImg
          })
        })
        const data = await res.json()
        this.pokedex = this.pokedex.map( poke => poke.id === newPoke.id ? {...poke, pokemonName:data.pokemonName, pokemonWeight:data.pokemonWeight, pokemonHeight:data.pokemonHeight, pokemonType:data.pokemonType} : poke  )
        this.isEdit = !this.isEdit
        this.editpokedex = {}
        console.log('Edit Successful')
      }catch(e){
        console.log(`Error: ${e}`)
      }
    }
  },
  async created() {
    this.pokedex = await this.getPokeData();
  },
};
</script>