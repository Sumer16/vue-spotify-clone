<template>
  <div class="bg-dark h-screen">
    <div class="flex" style="height: 88vh">
      <Sidebar :pages="pages" :albums="albums" />
      
      <div class="w-full h-full relative">
        <Header />

        <div></div>
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
        { id: 'radio', name: 'Radio', icon: 'radio' },
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
      ]
    }
  },
  methods: {

  }
}
</script>
