<template>
  <div class="w-full sticky top-0 px-5 py-4 flex items-center justify-between">
    <div class="flex items-center">
      <button
        class="rounded-full bg-black w-8 h-8 text-white focus:outline-none mr-3 hover:bg-gray-800"
      >
        <i class="material-icons p-1">keyboard_arrow_left</i>
      </button>
      <button class="rounded-full bg-black w-8 h-8 text-white focus:outline-none hover:bg-gray-800">
        <i class="material-icons p-1">keyboard_arrow_right</i>
      </button>
    </div>
    <div class="relative">
      <button
        v-on:click="showDropDown = !showDropDown"
        class="bg-light focus:outline-none rounded-full py-1 px-2 flex items-center transition duration-200 ease-linear hover:bg-gray-700"
      >
        <i class="material-icons rounded-full h-6 w-6 mr-2">person</i>
        <p class="text-white font-semibold text-xs mr-3">John Doe</p>
        <i v-if="showDropDown === false" class="material-icons text-white">arrow_drop_down</i>
        <i v-if="showDropDown === true" class="material-icons text-white">arrow_drop_up</i>
      </button>
      <div
        v-if="showDropDown"
        class="absolute bg-light p-2 w-full rounded mt-1 transition-all duration-500 ease-in-out"
      >
        <button
          v-on:click="showDropDown = false"
          class="focus:outline-none w-full text-sm py-2 text-lightest hover:text-white border-b border-gray-300 opacity-75 hover:opacity-100"
        >Account</button>
        <button
          v-on:click="showDropDown = false"
          class="focus:outline-none w-full text-sm py-2 text-lightest hover:text-white border-b border-light opacity-75 hover:opacity-100"
        >Log Out</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      showDropDown: false,
    };
  },
};
</script>