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

    <div class="w-full bg-light" style="height: 12vh">

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
      ]
    }
  },
  methods: {

  }
}
</script>
