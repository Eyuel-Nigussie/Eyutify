<script setup>
  import { ref, onMounted } from 'vue'
  import { RouterLink, RouterView } from 'vue-router'
  import MenuItem from './components/MenuItem.vue';
  import MusicPlayer from './components/MusicPlayer.vue'
  import ChevronUp from 'vue-material-design-icons/ChevronUp.vue';
  import ChevronDown from 'vue-material-design-icons/ChevronDown.vue';
  import ChevronRight from 'vue-material-design-icons/ChevronRight.vue';
  import ChevronLeft from 'vue-material-design-icons/ChevronLeft.vue';
  import { useSongStore } from './stores/song'
  import { storeToRefs } from 'pinia';
  const useSong = useSongStore()
  const { isPlaying, currentTrack } = storeToRefs(useSong)
  onMounted(() => { isPlaying.value = false })
  let openMenu = ref(false)
</script>

<template>
    <div class="vvv">

        <aside class="flex flex-col items-center w-16 h-screen py-8 overflow-y-auto  border-r rtl:border-l rtl:border-r-0 bg-[#24101c] border-gray-700 md:hidden">
            <nav class="flex flex-col flex-1 space-y-6">
                <a href="/">
                    <img class="w-auto h-6 " src="../public/images/icons/spotify-logo.png" alt="">
                </a>

                <a href="/search" class="p-1.5  focus:outline-nones transition-colors duration-200 rounded-lg text-gray-200 ">
                    <img class="w-auto h-6 pl-[8px] " src="../public/images/icons/search-inactive.png" alt="">
                </a>

                <a href="/library" class="p-1.5  focus:outline-nones transition-colors duration-200 rounded-lg text-gray-200 ">
                    <img class="w-auto h-6 pl-[8px]" src="../public/images/icons/library-inactive.png" alt="">
                </a>

                <a href="#" class="p-1.5  focus:outline-nones transition-colors duration-200 rounded-lg text-gray-200 ">
                    <img class="w-auto h-6 pl-[8px]" src="../public/images/icons/playlist-inactive.png" alt="">
                </a>

                <a href="#" class="pl-[8px] text-gray-700 focus:outline-nones transition-colors duration-200 rounded-lg dark:text-gray-200 dark:hover:bg-gray-800 hover:bg-gray-100">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M3 3v1.5M3 21v-6m0 0l2.77-.693a9 9 0 016.208.682l.108.054a9 9 0 006.086.71l3.114-.732a48.524 48.524 0 01-.005-10.499l-3.11.732a9 9 0 01-6.085-.711l-.108-.054a9 9 0 00-6.208-.682L3 4.5M3 15V4.5" />
                    </svg>
                </a>

                <a href="#" class="pl-[8px]  focus:outline-nones transition-colors duration-200 rounded-lg text-gray-200  hover:bg-gray-100">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M15 19.128a9.38 9.38 0 002.625.372 9.337 9.337 0 004.121-.952 4.125 4.125 0 00-7.533-2.493M15 19.128v-.003c0-1.113-.285-2.16-.786-3.07M15 19.128v.106A12.318 12.318 0 018.624 21c-2.331 0-4.512-.645-6.374-1.766l-.001-.109a6.375 6.375 0 0111.964-3.07M12 6.375a3.375 3.375 0 11-6.75 0 3.375 3.375 0 016.75 0zm8.25 2.25a2.625 2.625 0 11-5.25 0 2.625 2.625 0 015.25 0z" />
                    </svg>
                </a>
            </nav>

            <div class="flex flex-col space-y-6">
                <a href="#" class="p-1.5 focus:outline-nones transition-colors duration-200 rounded-lg text-gray-200 hover:bg-gray-100">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M16.712 4.33a9.027 9.027 0 011.652 1.306c.51.51.944 1.064 1.306 1.652M16.712 4.33l-3.448 4.138m3.448-4.138a9.014 9.014 0 00-9.424 0M19.67 7.288l-4.138 3.448m4.138-3.448a9.014 9.014 0 010 9.424m-4.138-5.976a3.736 3.736 0 00-.88-1.388 3.737 3.737 0 00-1.388-.88m2.268 2.268a3.765 3.765 0 010 2.528m-2.268-4.796a3.765 3.765 0 00-2.528 0m4.796 4.796c-.181.506-.475.982-.88 1.388a3.736 3.736 0 01-1.388.88m2.268-2.268l4.138 3.448m0 0a9.027 9.027 0 01-1.306 1.652c-.51.51-1.064.944-1.652 1.306m0 0l-3.448-4.138m3.448 4.138a9.014 9.014 0 01-9.424 0m5.976-4.138a3.765 3.765 0 01-2.528 0m0 0a3.736 3.736 0 01-1.388-.88 3.737 3.737 0 01-.88-1.388m2.268 2.268L7.288 19.67m0 0a9.024 9.024 0 01-1.652-1.306 9.027 9.027 0 01-1.306-1.652m0 0l4.138-3.448M4.33 16.712a9.014 9.014 0 010-9.424m4.138 5.976a3.765 3.765 0 010-2.528m0 0c.181-.506.475-.982.88-1.388a3.736 3.736 0 011.388-.88m-2.268 2.268L4.33 7.288m6.406 1.18L7.288 4.33m0 0a9.024 9.024 0 00-1.652 1.306A9.025 9.025 0 004.33 7.288" />
                    </svg>
                </a>

                <a href="#" class="p-1.5  focus:outline-nones transition-colors duration-200 rounded-lg text-gray-200bg-gray-800 bg-gray-100">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M10.343 3.94c.09-.542.56-.94 1.11-.94h1.093c.55 0 1.02.398 1.11.94l.149.894c.07.424.384.764.78.93.398.164.855.142 1.205-.108l.737-.527a1.125 1.125 0 011.45.12l.773.774c.39.389.44 1.002.12 1.45l-.527.737c-.25.35-.272.806-.107 1.204.165.397.505.71.93.78l.893.15c.543.09.94.56.94 1.109v1.094c0 .55-.397 1.02-.94 1.11l-.893.149c-.425.07-.765.383-.93.78-.165.398-.143.854.107 1.204l.527.738c.32.447.269 1.06-.12 1.45l-.774.773a1.125 1.125 0 01-1.449.12l-.738-.527c-.35-.25-.806-.272-1.203-.107-.397.165-.71.505-.781.929l-.149.894c-.09.542-.56.94-1.11.94h-1.094c-.55 0-1.019-.398-1.11-.94l-.148-.894c-.071-.424-.384-.764-.781-.93-.398-.164-.854-.142-1.204.108l-.738.527c-.447.32-1.06.269-1.45-.12l-.773-.774a1.125 1.125 0 01-.12-1.45l.527-.737c.25-.35.273-.806.108-1.204-.165-.397-.505-.71-.93-.78l-.894-.15c-.542-.09-.94-.56-.94-1.109v-1.094c0-.55.398-1.02.94-1.11l.894-.149c.424-.07.765-.383.93-.78.165-.398.143-.854-.107-1.204l-.527-.738a1.125 1.125 0 01.12-1.45l.773-.773a1.125 1.125 0 011.45-.12l.737.527c.35.25.807.272 1.204.107.397-.165.71-.505.78-.929l.15-.894z" />
                        <path stroke-linecap="round" stroke-linejoin="round" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" />
                    </svg>
                </a>

                <a href="#">
                    <img class="object-cover w-8 h-8 rounded-full" src="https://user-images.githubusercontent.com/105924760/213940591-624b39f3-b43a-4b31-8835-df7fcc001ea7.png" alt="" />
                </a>
            </div>
        </aside>


        <div 
          id="TopNav"
          class="
            w-[calc(100%-60px)]
            md:w-[calc(100%-175px)] 
            h-[60px] 
            fixed 
            right-0 
            z-20 
            bg-[#160213] 
            bg-opacity-80 
            flex 
            items-center 
            justify-between
          "
        >
    
            <div class="flex items-center ml-6">
                <button type="button" class="rounded-full bg-black p-[1px] cursor-pointer">
                    <ChevronLeft fillColor="#FFFFFF" :size="30" />
                </button>
                <button type="button" class="rounded-full bg-black p-[1px] hover:bg-[#] ml-4 cursor-pointer">
                    <ChevronRight fillColor="#FFFFFF" :size="30" />
                </button>
               
            </div>

            <button @click="openMenu = !openMenu" :class="openMenu ? 'bg-[#824983]' : 'bg-black'"
                class="bg-[#140210cc] hover:bg-[#7a3d6d] rounded-full p-0.5 mr-8 mt-0.5 cursor-pointer">
                <div class="flex items-center ">
                    <img 
                      class="rounded-full mx-1  " 
                      width="27"
                      src="https://user-images.githubusercontent.com/105924760/213940591-624b39f3-b43a-4b31-8835-df7fcc001ea7.png"
                    >
                    <div class="text-white text-[14px] ml-1.5 font-semibold">Eyuel Nigussie</div>
                    <ChevronDown v-if="!openMenu" @click="openMenu = true" fillColor="#FFFFFF" :size="25" />
                    <ChevronUp v-else @click="openMenu = false" fillColor="#FFFFFF" :size="25" />
                </div>
            </button>

            <span v-if="openMenu"
                class="fixed w-[190px] bg-[#41293a] shadow-2xl z-50 rounded-sm top-[52px] right-[35px] p-1 cursor-pointer">
                <ul class="text-gray-200 font-semibold text-[14px]">
                    <li class="px-3 py-2.5 hover:bg-[#bd5da474] border-b border-b-gray-600">Profile</li>
                    <li class="px-3 py-2.5 hover:bg-[#bd5da474]">Log out</li>
                </ul>
           </span>
     </div>

     

        <!-- big sidebar -->
        <div id="SideNav" class="hidden md:block h-[100%] p-6 :w-[240px] fixed z-50 bg-[#0e010a]">
            <RouterLink to="/">
              <img width="125" src="/images/icons/spotify-logo.png">
            </RouterLink>
            <div class="my-8"></div>
            <ul>
                <RouterLink to="/">
                    <MenuItem class="ml-[1px]" :iconSize="23" name="Home" iconString="home" pageUrl="/" />
                </RouterLink>
                <RouterLink to="/search">
                    <MenuItem class="ml-[1px]" :iconSize="24" name="Search" iconString="search" pageUrl="/search" />
                </RouterLink>
                <RouterLink to="/library">
                    <MenuItem class="ml-[2px]" :iconSize="23" name="Your Library" iconString="library" pageUrl="/library" />
                </RouterLink>
                <div class="py-3.5"></div>
                <MenuItem :iconSize="24" name="Create Playlist" iconString="playlist" pageUrl="/playlist" />
                <MenuItem class="-ml-[1px]" :iconSize="27" name="Liked Songs" iconString="liked" pageUrl="/liked" />
            </ul>
            <div class="border-b border-b-gray-700"></div>
            <ul>
                <li class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white">My Playlist #1</li>
                <li class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white">My Playlist #2</li>
                <li class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white">My Playlist #3</li>
                <li class="font-semibold text-[13px] mt-3 text-gray-300 hover:text-white">My Playlist #4</li>
            </ul>
        </div>
    </div>



    <div
        class="
            fixed
            right-0
            top-0
            w-[calc(100%-60px)] 
            md:w-[calc(100%-175px)] 
            overflow-auto
            h-full
            bg-gradient-to-b
            from-[#500029ec]
            to-[#1e0010]
        "
    >
        <div class="mt-[70px]"></div>
        <RouterView />
        <div class="mb-[100px]"></div>
    </div>

    <MusicPlayer v-if="currentTrack"/>
</template>

<style>
.vvv{
background-color: #090004;
background-image: url("data:image/svg+xml,%3Csvg width='64' height='64' viewBox='0 0 64 64' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M8 16c4.418 0 8-3.582 8-8s-3.582-8-8-8-8 3.582-8 8 3.582 8 8 8zm0-2c3.314 0 6-2.686 6-6s-2.686-6-6-6-6 2.686-6 6 2.686 6 6 6zm33.414-6l5.95-5.95L45.95.636 40 6.586 34.05.636 32.636 2.05 38.586 8l-5.95 5.95 1.414 1.414L40 9.414l5.95 5.95 1.414-1.414L41.414 8zM40 48c4.418 0 8-3.582 8-8s-3.582-8-8-8-8 3.582-8 8 3.582 8 8 8zm0-2c3.314 0 6-2.686 6-6s-2.686-6-6-6-6 2.686-6 6 2.686 6 6 6zM9.414 40l5.95-5.95-1.414-1.414L8 38.586l-5.95-5.95L.636 34.05 6.586 40l-5.95 5.95 1.414 1.414L8 41.414l5.95 5.95 1.414-1.414L9.414 40z' fill='%239C92AC' fill-opacity='0.4' fill-rule='evenodd'/%3E%3C/svg%3E");
}

</style>