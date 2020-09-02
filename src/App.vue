<template>
  <div class="bg-dark h-screen">
    <div class="flex" style="height: 88vh">
      <div class="w-56 bg-black h-full flex-none">
        <div class="m-6">
          <img src="spotifyLogo.png" class="h-10" alt="">
        </div>
        <div class="mx-2 mb-5">
          <button v-for="page in pages" v-on:click="setID = page.id" :key="page.id" :class="`w-full text-sm font-semibold rounded px-3 py-2 flex items-center justify-start ${setID === page.id ? 'bg-light text-white' : 'text-lightest'} hover:font-bold hover:bg-gray-100 hover:bg-opacity-25`">
            <i class="material-icons">{{ page.icon }}</i>
            <p class="ml-3"> {{ page.name }} </p>
          </button>
        </div>
        <div class="mx-5">
          <h1 class="text-xs mb-3 text-lightest tracking-widest uppercase">Playlists</h1>
          <button class="flex items-center justify-start opacity-75 hover:opacity-100 mb-2">
            <i class="material-icons bg-white mr-3 p-1">add</i>
            <p class="text-sm text-white font-semibold">Create Playlist</p>
          </button>
          <button class="flex items-center justify-start opacity-75 hover:opacity-100 mb-2">
            <i class="material-icons bg-purple-500 mr-3 p-1 text-white">favorite</i>
            <p class="text-sm text-white font-semibold">Create Playlist</p>
          </button>
        </div>
      </div>

      <div class="w-full h-full relative">
        <div class="w-full sticky top-0 p-2">

        </div>
      </div>
    </div>

    <div class="w-full bg-light" style="height: 12vh">

    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      pages: [
        { id: 'home', name: 'Home', icon: 'home' },
        { id: 'search', name: 'Search', icon: 'search' },
        { id: 'library', name: 'Your Library', icon: 'bar_chart' }
      ],
      setID: 'home'
    }
  },
  methods: {

  }
}
</script>
