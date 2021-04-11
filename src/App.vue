<template>
  <div class="h-screen bg-gray-50">

    <nav class="relative z-10 bg-white shadow-md">
      <div
        class="flex justify-center text-sm font-bold font-sans text-gray-400">
        
        <router-link to="/">
          <div class="w-28 text-center hover:bg-gray-500 hover:text-white pb-2">
            <i class="material-icons mt-2">home</i>
            <p>HOME</p>
          </div>
        </router-link>

        <div
          class="w-28 text-center hover:bg-red-600 hover:text-white text-gray-400 pb-2">
          <i class="material-icons mt-2">catching_pokemon</i>
          <p>Pokédex</p>
        </div>

        <div
          class="w-28 text-center hover:bg-blue-500 hover:text-white text-gray-400 pb-2">
          <i class="material-icons mt-2">info</i>
          <p>About</p>
        </div>
      </div>
    </nav>

    <div class="relative z-0 w-2/3 mx-auto items-center text-center bg-red-400 shadow-lg">
      <router-view />
    </div>
  </div>

</template>

