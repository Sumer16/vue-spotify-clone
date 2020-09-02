<template>
  <div class="w-56 bg-black h-full flex-none">
    <div class="m-6">
      <img src="spotifyLogo.png" class="h-10" alt />
    </div>
    <div class="mx-2 mb-5">
      <button
        v-for="page in pages"
        v-on:click="setID = page.id"
        :key="page.id"
        :class="`w-full text-sm focus:outline-none font-semibold rounded px-3 py-2 flex items-center justify-start ${setID === page.id ? 'bg-light text-white' : 'text-lightest'} hover:font-bold hover:bg-gray-100 hover:bg-opacity-25`"
      >
        <i class="material-icons">{{ page.icon }}</i>
        <p class="ml-3">{{ page.name }}</p>
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
        <p class="text-sm text-white font-semibold">Liked Songs</p>
      </button>
      <div class="h-px w-full bg-light my-3"></div>
    </div>
    <div class="mx-5 h-auto">
      <div class="w-full overflow-y-scroll scroll-thumb:bg-gray-900" style="height: 23rem">
        <p
          v-for="album in albums"
          :key="album.name"
          class="text-lightest hover:text-white text-sm py-1"
        >{{ album.name }}</p>
      </div>
      <button class="flex items-center justify-start text-lightest hover:text-white py-2">
        <i class="material-icons mr-3 rounded-full border text-sm border-lightest">arrow_downward</i>
        <p class="text-sm font-semibold">Install App</p>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Sidebar',
  props: ['pages', 'albums']
};
</script>