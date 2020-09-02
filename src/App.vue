<template>
  <div class="bg-dark h-screen">
    <div class="flex" style="height: 88vh">
      <Sidebar :pages="pages" :albums="albums" />
      
      <div class="w-full h-full relative overflow-y-scroll">
        <Header />

        <div class="px-6 py-3">
          <div class="flex items-center justify-between">
            <h1 class="pl-2 text-2xl font-semibold text-white tracking-wider hover:underline">Recently Played</h1>
            <h2 class="pr-8 pt-4 text-xs text-lightest uppercase tracking-wider hover:underline mb-3">See All</h2>
          </div>
          <div class="w-full flex flex-wrap">
            <div v-for="recent in recents" :key="recent.title" class="p-2 w-48 relative">
              <div class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100">
                <div class="bg-green rounded-full h-10 w-10 flex items-center justify-center">
                  <i class="material-icons text-white text-2xl">play_arrow</i>
                </div>
              </div>
              <div class="bg-light w-full h-auto p-5 rounded-lg shadow-md">
                <img :src="recent.src" class="h-auto w-full shadow mb-2" alt="">
                <h1 class="text-sm font-semibold text-white tracking-wide"> {{ recent.title }}</h1>
                <h2 class="text-xs text-lightest tracking-wide pb-5">{{ recent.artist }}</h2>
              </div>
            </div>
          </div>
        </div>

        <div class="px-6 py-3">
          <div class="pl-2">
            <h1 class="text-2xl font-semibold text-white tracking-wider hover:underline">Made for John</h1>
            <h2 class="py-2 text-xs text-lightest uppercase tracking-wider">Get better recommendations the more you listen.</h2>
          </div>
          <div class="w-full flex flex-wrap">
            <div v-for="custom in customs" :key="custom.title" class="p-2 w-48 relative">
              <div class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100">
                <div class="bg-green rounded-full h-10 w-10 flex items-center justify-center">
                  <i class="material-icons text-white text-2xl">play_arrow</i>
                </div>
              </div>
              <div class="bg-light w-full h-auto p-5 rounded-lg shadow-md">
                <img :src="custom.src" class="h-auto w-full shadow mb-2" alt="">
                <h1 class="text-sm font-semibold text-white tracking-wide"> {{ custom.title }}</h1>
                <h2 class="text-xs text-lightest tracking-wide pb-5">{{ custom.artist }}</h2>
              </div>
            </div>
          </div>
        </div>

        <div class="px-6 py-3">
          <div class="flex items-center justify-between">
            <h1 class="pl-2 text-2xl font-semibold text-white tracking-wider hover:underline">Your top podcasts</h1>
            <h2 class="pr-8 pt-4 text-xs text-lightest uppercase tracking-wider hover:underline mb-3">See All</h2>
          </div>
          <div class="w-full flex flex-wrap">
            <div v-for="podcast in podcasts" :key="podcast.title" class="p-2 w-48 relative">
              <div class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100">
                <div class="bg-green rounded-full h-10 w-10 flex items-center justify-center">
                  <i class="material-icons text-white text-2xl">play_arrow</i>
                </div>
              </div>
              <div class="bg-light w-full h-auto p-5 rounded-lg shadow-md">
                <img :src="podcast.src" class="h-auto w-full shadow mb-2" alt="">
                <h1 class="text-sm font-semibold text-white tracking-wide"> {{ podcast.title }}</h1>
                <h2 class="text-xs text-lightest tracking-wide pb-5">{{ podcast.artist }}</h2>
              </div>
            </div>
          </div>
        </div>
        
      </div>
    </div>

    <div class="w-full flex items-center justify-between px-3 bg-light border-t border-dark" style="height: 12vh">
      <div class="flex items-center w-1/4">
        <div>
          <h1 class="text-sm text-white tracking-wide">Affection</h1>
          <h2 class="text-xs text-lightest tracking-wide">Cigarettes after Sex</h2>
        </div>
        <i class="material-icons text-xl text-green mx-4">favorite</i>
        <i class="material-icons text-xl text-lightest hover:text-white">picture_in_picture_alt</i>
      </div>
      <div class="flex flex-col justify-center w-2/4 items-center">
        <div class="flex items-center">
          <button class="mx-5 text-lightest hover:text-white"><i class="material-icons text-lg">shuffle</i></button>
          <button class="text-lightest hover:text-white"><i class="material-icons text-lg">skip_previous</i></button>
          <button v-on:click.prevent="playSong('affection.mp3')" class="rounded-full h-8 w-8 flex items-center justify-center mx-5 border border-lightest text-lightest hover:text-white"><i v-if="pause === false" class="material-icons">play_arrow</i><i v-if="pause === true" class="material-icons">pause</i></button>
          <button class="text-lightest hover:text-white"><i class="material-icons text-lg">skip_next</i></button>
          <button class="mx-5 text-lightest hover:text-white"><i class="material-icons text-lg">repeat</i></button>
        </div>
        <div class="w-3/4 flex items-center justify-center mt-3">
          <p class="text-xs text-lightest mr-1">0:28</p>
          <div class="w-full h-1 bg-dark rounded-full flex items-center">
            <div class="h-1 rounded-full bg-green" style="width: 18%;"></div>
            <div class="h-3 w-3 bg-white rounded-full -ml-1 shadow"></div>
          </div>
          <p class="text-xs text-lightest ml-1">2:40</p>
        </div>
      </div>
      <div class="flex items-center w-1/4 justify-end">
        <i class="material-icons text-lightest hover:text-white">playlist_play</i>
        <i class="material-icons text-xl text-lightest mx-3 hover:text-white">important_devices</i>
        <i class="material-icons text-xl text-lightest hover:text-white">volume_up</i>
        <div class="w-20 ml-1 bg-lightest rounded-full h-1">

        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Sidebar from '@/components/Sidebar.vue'
import Header from '@/components/Header.vue'

export default {
  name: 'App',
  components: {
    Sidebar,
    Header
  },
  data() {
    return {
      pages: [
        { id: 'home', name: 'Home', icon: 'home' },
        { id: 'search', name: 'Search', icon: 'search' },
        { id: 'library', name: 'Your Library', icon: 'bar_chart' },
      ],
      albums: [
        { name: 'drive' },
        { name: 'zhu' },
        { name: 'All New Indie' },
        { name: 'Mellow' },
        { name: 'Classic Road Trip Songs' },
        { name: 'Lana Del Rey Radio' },
        { name: 'Lofi Coding' },
        { name: 'Work From Home' },
        { name: 'Peaceful Guitar' },
        { name: 'Peaceful Piano' },
        { name: 'Motivational' },
        { name: 'Programming & Engineering' },
        { name: 'Peace Out' },
        { name: 'Shawn Mendes' },
        { name: 'Entry to Hell' },
        { name: 'Exit From Heaven' },
        { name: 'Agent Vinod' },
        { name: 'Laughter' },
        { name: 'Zen Meditate' },
      ],
      recents: [
        { src: 'bollywood.jpg', title: 'Bollywood Rocks', artist: 'By Spotify'},
        { src: 'concentration.jpg', title: 'Concentrate Study', artist: 'By Spotify'},
        { src: 'lofing.jpg', title: 'Lofing Beats', artist: 'By Spotify'},
        { src: 'piano.jpg', title: 'Peaceful Piano', artist: 'By Spotify'},
        { src: 'study.jpg', title: 'Study Motivation', artist: 'By Spotify'},
        { src: 'bollywood.jpg', title: 'Bollywood Mocks', artist: 'By Spotify'},
        { src: 'lofing.jpg', title: 'Lofing Meats', artist: 'By Spotify'},
        { src: 'study.jpg', title: 'Art Motivation', artist: 'By Spotify'},
        { src: 'piano.jpg', title: 'Peaceful Guitar', artist: 'By Spotify'},
      ],
      customs: [
        { src: 'bollywood.jpg', title: 'Bollywood Rocks', artist: 'By Spotify'},
        { src: 'concentration.jpg', title: 'Concentrate Study', artist: 'By Spotify'},
        { src: 'lofing.jpg', title: 'Lofing Beats', artist: 'By Spotify'},
        { src: 'piano.jpg', title: 'Peaceful Piano', artist: 'By Spotify'},
        { src: 'study.jpg', title: 'Study Motivation', artist: 'By Spotify'},
      ],
      podcasts: [
        { src: 'bollywood.jpg', title: 'Bollywood Rocks', artist: 'By Spotify'},
        { src: 'concentration.jpg', title: 'Concentrate Study', artist: 'By Spotify'},
        { src: 'lofing.jpg', title: 'Lofing Beats', artist: 'By Spotify'},
        { src: 'piano.jpg', title: 'Peaceful Piano', artist: 'By Spotify'},
        { src: 'study.jpg', title: 'Study Motivation', artist: 'By Spotify'},
        { src: 'bollywood.jpg', title: 'Tollywood Rocks', artist: 'By Spotify'},
        { src: 'lofing.jpg', title: 'Lofing Meats', artist: 'By Spotify'},
        { src: 'concentration.jpg', title: 'Concentrate Art', artist: 'By Spotify'},
      ],
      pause: false
    }
  },
  methods: {
    playSong(song) {
      if(song) {
        this.pause = !this.pause;
        const audio = new Audio(song);
        audio.play();
      }
    }
  }
}
</script>
