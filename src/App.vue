<template>
  <div class="h-screen bg-gray-50">
    <nav>
      <div class="flex justify-center text-sm font-bold font-sans text-gray-400 ">
        <router-link to="/">
          <div class="w-28 text-center hover:bg-yellow-400 hover:text-white pb-2 rounded-b-md" :class="[currentpage === 'home' ? 'bg-yellow-400 text-white ' : 'bg-none']" >
            <i class="material-icons mt-2">home</i>
            <p>HOME</p>
          </div>
        </router-link>


        <router-link to="/pokedex">
          <div class="w-28 text-center hover:bg-red-600 hover:text-white pb-2 rounded-b-md" :class="[currentpage === 'pokedex' ? 'bg-red-600 text-white ' : 'bg-none']">  
            <i class="material-icons mt-2">catching_pokemon</i>
            <p>Pokédex</p>
          </div>
        </router-link>

         <router-link to="/about">
          <div class="w-28 text-center hover:bg-blue-500 hover:text-white pb-2 rounded-b-md" :class="[currentpage === 'about' ? 'bg-blue-500 text-white ' : 'bg-none']">
            <i class="material-icons mt-2">info</i>
            <p>About</p>
          </div>
         </router-link>
      </div>
    </nav>

    <div class="h-auto w-2/3 mx-auto items-center text-center">
      <router-view/>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return{
      currentpage : null,
      dburl: 'http://localhost:5000/pokedex'
    }
  },
  methods:{
    changePage(namePage){ //this method make a chenge currentnamepage 
      this.currentpage = namePage
      console.log(`currentpage: ${this.currentpage}`)
    }
  }
}
</script>


