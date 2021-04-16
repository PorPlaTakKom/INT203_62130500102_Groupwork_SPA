<template>
  <div class="flex justify-center w-full mx-auto">
    <form @submit.prevent="registerFrom">

      <div class="flex flex-col pb-3">
          <label for="pekemonName" class="font-bold text-white text-xl p-1">Pokemon Name</label>
          <input class="focus:outline-none p-1 w-5/12 rounded-md mx-auto"
          id="pokemonName"
          type="text"
          placeholder="Pikachu"
          v-model="pokemonName"/>
      </div>

      <div class="flex justify-center space-x-2">
          <label for="height" class="font-bold text-white text-xl">Height:</label>
          <input class="focus:outline-none p-1 w-2/12 rounded-md" 
          id="height"
          type="float"
          placeholder="50"
          v-model="pokemonHeight"/>

          <label for="weight" class="font-bold text-white text-xl">Weight:</label>
          <input class="focus:outline-none w-2/12 rounded-md p-1"
          id="weight"
          type="float"
          placeholder="15.2"
          v-model="pokemonWeight"/>
      </div>

      <div class="flex flex-col">
          <label for="type" class="font-bold text-white text-xl m-1">Pokemon Type</label>
          <input class="focus:outline-none p-1 w-5/12 rounded-md mx-auto"
          id="type"
          type="text"
          placeholder="Electric"
          v-model="pokemonType"/>
      </div>

      <div class="flex flex-col">
          <label for="img" class="font-bold text-white text-xl m-1">Pokemon Image-Link</label>
          <input class="focus:outline-none p-1 w-5/12 rounded-md mx-auto"
          id="img"
          type="text"
          placeholder="https://assets.pokemon.com/assets/cms2/img/pokedex/full/025.png"
          v-model="pokemonImg"/>
      </div>

      <div class="mt-5">
         <button class="bg-blue-400 rounded-md p-1 text-white font-bold focus:outline-none" type="submit" >Summit</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "RegisForm",
  data() {
    return {
      pokemonName: '',
      pokemonHeight: '',
      pokemonWeight: '',
      pokemonType:'',
      pokemonImg: '',
      pokedex: []
    };
  },
  methods: {
    registerFrom() {

      if(this.pokemonName !== '' && this.pokemonHeight !== '' && this.pokemonWeight !== ''  && this.pokemonType !== '' && this.pokedex !== null){
              this.addPokedata({
                pokemonName: this.pokemonName,
                pokemonHeight: this.pokemonHeight,
                pokemonWeight: this.pokemonWeight,
                pokemonType: this.pokemonType,
                pokemonImg: this.pokemonImg
              })
              location.reload()

              // this.pokemonName = ''
              // this.pokemonHeight = ''
              // this.pokemonWeight = ''
              // this.pokemonType = ''
              // this.pokemonImg = ''
      }else{
        console.log('Summit is not data, Can not push data to database ')
      }
      
    },
    async addPokedata(pekeData){
      try{
        const pokedata = {
          pokemonName: pekeData.pokemonName,
          pokemonHeight: pekeData.pokemonHeight,
          pokemonWeight: pekeData.pokemonWeight,
          pokemonType: pekeData.pokemonType,
          pokemonImg: pekeData.pokemonImg
          }
        const res = await fetch('http://localhost:5000/pokedex',
        {
        method: 'POST',
        headers:{
          'content-type': 'application/json'
        },
        body: JSON.stringify(pokedata)
        })
        this.pokedex.push(await res.json())
      }catch(error){
        console.log(`error : ${error}`)
      }
    }
  }
}
</script>