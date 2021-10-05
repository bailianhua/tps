<template>
  <div class="app overflow-y-auto">
    <TransitionRoot appear :show="isOpen" as="template">
      <Dialog as="div" @close="closeModal">
        <div class="fixed inset-0 z-10 overflow-y-auto">
          <div class="min-h-screen px-4 text-center">
            <TransitionChild
              as="template"
              enter="duration-300 ease-in"
              enter-from="opacity-0"
              enter-to="opacity-100"
              leave="duration-200 ease-in"
              leave-from="opacity-100"
              leave-to="opacity-0"
            >
              <DialogOverlay class="fixed inset-0 bg-opacity-30 bg-black" />
            </TransitionChild>
            <div
              class="inline-block w-full max-w-md p-6 my-8 overflow-hidden text-left align-middle transition-all transform bg-white shadow-xl rounded-2xl"
            >
              <transition name="fade" mode="out-in">
                <DialogTitle
                  as="h3"
                  class="text-lg font-medium leading-6 text-gray-900 inline-flex"
                  v-if="charDataloading"
                >
                  Casting
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    class="h-6 w-6 ml-1 animate-spin transform rotate-180"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      stroke-width="2"
                      d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15"
                    />
                  </svg>
                </DialogTitle>
              </transition>

              <div
                v-if="charDataloading"
                class="border border-blue-300 shadow rounded-md p-4 max-w-sm w-full mx-auto"
              >
                <div class="animate-pulse flex space-x-4">
                  <div class="rounded-full bg-blue-400 h-12 w-12"></div>
                  <div class="flex-1 space-y-4 py-1">
                    <div class="h-4 bg-blue-400 rounded w-3/4"></div>
                    <div class="space-y-2">
                      <div class="h-4 bg-blue-400 rounded"></div>
                      <div class="h-4 bg-blue-400 rounded w-5/6"></div>
                    </div>
                  </div>
                </div>
              </div>

              <div
                v-if="!charDataloading"
                class="border border-blue-300 shadow rounded-md p-4 max-w-sm w-full mx-auto"
              >
                <div class="flex space-x-4">
                  <img
                    :src="charData.Character.Avatar"
                    class="rounded-full bg-blue-400 h-12 w-12 self-center"
                  />
                  <div class="flex-1 py-1">
                    <div class="rounded w-full">{{ charData.Character.Name }}</div>
                    <div
                      class="font-sans italic text-xs tracking-tighter leading-tight"
                    >FC : {{ charData.Character.FreeCompanyName }}</div>
                    <div
                      class="font-sans italic text-xs tracking-tighter leading-tight"
                    >{{ charData.Character.Server }}</div>
                  </div>
                </div>
              </div>

              <div
                v-if="!charDataloading"
                class="relative border-blue-300 shadow rounded-md max-w-sm w-full mx-auto"
              >
                <img :src="charData.Character.Portrait" class="rounded-sm bg-blue-400" />
                <div class="absolute top-4 left-1 flex flex-col space-y-6 overflow-hidden">
                  <div
                    class="bg-cover rounded-lg p-6"
                    :style="`background-image: url('https://xivapi.com/${charData.Character.GearSet.Gear.MainHand.Item.Icon}')`"
                  ></div>
                  <div
                    class="bg-cover rounded-lg p-6"
                    :style="`background-image: url('https://xivapi.com/${charData.Character.GearSet.Gear.Head.Item.Icon}')`"
                  ></div>
                  <div
                    class="bg-cover rounded-lg p-6"
                    :style="`background-image: url('https://xivapi.com/${charData.Character.GearSet.Gear.Body.Item.Icon}')`"
                  ></div>
                  <div
                    class="bg-cover rounded-lg p-6"
                    :style="`background-image: url('https://xivapi.com/${charData.Character.GearSet.Gear.Hands.Item.Icon}')`"
                  ></div>
                  <div
                    class="bg-cover rounded-lg p-6"
                    :style="`background-image: url('https://xivapi.com/${charData.Character.GearSet.Gear.Legs.Item.Icon}')`"
                  ></div>
                  <div
                    class="bg-cover rounded-lg p-6"
                    :style="`background-image: url('https://xivapi.com/${charData.Character.GearSet.Gear.Feet.Item.Icon}')`"
                  ></div>
                </div>
                <div class="absolute top-4 right-1 flex flex-col space-y-6 overflow-hidden">
                  <div
                    class="bg-cover rounded-lg p-6"
                    :style="`background-image: url('https://xivapi.com/${charData.Character.GearSet.Gear.Earrings.Item.Icon}')`"
                  ></div>
                  <div
                    class="bg-cover rounded-lg p-6"
                    :style="`background-image: url('https://xivapi.com/${charData.Character.GearSet.Gear.Necklace.Item.Icon}')`"
                  ></div>
                  <div
                    class="bg-cover rounded-lg p-6"
                    :style="`background-image: url('https://xivapi.com/${charData.Character.GearSet.Gear.Bracelets.Item.Icon}')`"
                  ></div>
                  <div
                    class="bg-cover rounded-lg p-6"
                    :style="`background-image: url('https://xivapi.com/${charData.Character.GearSet.Gear.Ring1.Item.Icon}')`"
                  ></div>
                  <div
                    class="bg-cover rounded-lg p-6"
                    :style="`background-image: url('https://xivapi.com/${charData.Character.GearSet.Gear.Ring2.Item.Icon}')`"
                  ></div>
                </div>
                <div></div>
              </div>

              <div class="mt-4">
                <button
                  type="button"
                  class="inline-flex justify-center px-4 py-2 text-sm font-medium text-blue-900 bg-blue-100 border border-transparent rounded-md hover:bg-blue-200 focus:outline-none focus-visible:ring-2 focus-visible:ring-offset-2 focus-visible:ring-blue-500"
                  @click="closeModal"
                >Close window</button>
              </div>
            </div>
          </div>
        </div>
      </Dialog>
    </TransitionRoot>
    <TransitionRoot appear :show="newCard" as="template">
      <Dialog as="div" @close="newCard = !newCard">
        <div class="fixed inset-0 z-10 overflow-y-auto">
          <div class="min-h-screen px-4 text-center">
            <TransitionChild
              as="template"
              enter="duration-300 ease-in"
              enter-from="opacity-0"
              enter-to="opacity-100"
              leave="duration-200 ease-in"
              leave-from="opacity-100"
              leave-to="opacity-0"
            >
              <DialogOverlay class="fixed inset-0 bg-opacity-30 bg-black" />
            </TransitionChild>
            <div
              class="inline-block w-full max-w-md p-6 my-8 overflow-hidden text-left align-middle transition-all transform bg-white shadow-xl rounded-2xl"
            >
              <div class="border border-blue-300 shadow rounded-md p-4 max-w-sm w-full mx-auto">
                <div class>
                  <p>Name:</p>
                  <input type="text" class="rounded underline text-sm w-full" />
                </div>
                <div class="my-2">
                  <p>Twitter:</p>
                  <input type="text" class="rounded underline w-full font-sans" />
                </div>
                <div class="my-2">
                  <p>Twitch:</p>
                  <input type="text" class="rounded underline w-full font-sans" />
                </div>
                <div class="my-2">
                  <p>Youtube:</p>
                  <input type="text" class="rounded underline w-full font-sans" />
                </div>
              </div>
            </div>
          </div>
        </div>
      </Dialog>
    </TransitionRoot>
    <video-background
      :src="videoBackground.src"
      :muted="videoBackground.muted"
      :loop="videoBackground.loop"
      style="height: 100vh;"
      overlay="rgba(50, 50, 50, 0.7)"
    >
      <p
        class="animate-fade-in underline align-middle text-gray-100 text-center text-5xl tracking-tight pt-5"
        style="animation-delay: 1s;
        animation-fill-mode: forwards;
        opacity: 0;"
      >{{ title }}</p>
      <p
        class="animate-fade-in align-middle text-gray-100 text-center text-5xl font-black tracking-widest leading-relaxed"
        style="animation-delay: 2s;
        animation-fill-mode: forwards;
        opacity: 0;"
      >{{ teamTag }}</p>
      <p
        class="animate-fade-in italic align-middle text-gray-100 text-center text-2xl font-bold tracking-tight"
        style="animation-delay: 2s;
        animation-fill-mode: forwards;
        opacity: 0;"
      >{{ teamName }}</p>
      <div
        class="flex flex-wrap justify-center w-screen pt-10 overflow-y-auto gap-x-12 gap-y-8 md:gap-x-10 mx-auto pb-96 md:pb-60"
        style="height: 100%"
      >
        <Card
          cardName="SUPER PEASANT"
          bgImg="image/pld.png"
          profilePic="https://pbs.twimg.com/profile_images/1297155239133544453/598cnZFD_400x400.jpg"
          twitterSrc="https://twitter.com/PeasantXIV"
          animationDelay="3"
          lodeStone="6455202"
          v-on:detailClicked="openModal"
        ></Card>
        <Card
          cardName="SINDALF SINDALF"
          bgImg="image/drk.png"
          profilePic="https://pbs.twimg.com/profile_images/1188497791275847680/-DrQVbly_400x400.jpg"
          twitterSrc="https://twitter.com/Sindalf"
          animationDelay="3.5"
          lodeStone="1583960"
          v-on:detailClicked="openModal"
        ></Card>
        <Card
          cardName="KIONA LYNEAR"
          bgImg="image/whm.png"
          profilePic="https://cdn.discordapp.com/avatars/49249729237745664/acf02ccf4304a8706e1dac4af5ce455e.webp?size=128"
          twitterSrc="https://twitter.com/_Kionu_"
          youtubeSrc="https://www.youtube.com/user/xkadinx"
          animationDelay="4"
          lodeStone="2500630"
          v-on:detailClicked="openModal"
        ></Card>
        <Card
          cardName="ARA HOSHIZORA"
          bgImg="image/ast.png"
          profilePic="https://pbs.twimg.com/profile_images/1349807474031939587/gn7WB6FM_400x400.jpg"
          twitterSrc="https://twitter.com/Ara_Hoshizora"
          animationDelay="4.5"
          lodeStone="1826381"
          v-on:detailClicked="openModal"
        ></Card>
        <Card
          cardName="SHINA FLOREM"
          bgImg="image/nin.png"
          profilePic="https://pbs.twimg.com/profile_images/906667510971359232/vyy8dj7V_400x400.jpg"
          twitterSrc="https://twitter.com/yomikadoneko"
          animationDelay="5"
          lodeStone="8856251"
          v-on:detailClicked="openModal"
        ></Card>
        <Card
          cardName="PHANTOM ASSASSIN"
          bgImg="image/brd.png"
          profilePic="https://pbs.twimg.com/profile_images/1277703728078950400/W5Oc5BIk_400x400.png"
          twitterSrc="https://twitter.com/Phantom_xiv"
          animationDelay="5.5"
          lodeStone="8014568"
          v-on:detailClicked="openModal"
        ></Card>
        <Card
          cardName="SFIA PIRION"
          bgImg="image/blm.png"
          profilePic="https://pbs.twimg.com/profile_images/1196157469178744832/6RDSD2-P_400x400.jpg"
          twitterSrc="https://twitter.com/FFsfia"
          twitchSrc="https://www.twitch.tv/sfia"
          youtubeSrc="https://www.youtube.com/channel/UC5hfA-E66fLH9HVD5vuMdbQ"
          animationDelay="6"
          lodeStone="1549390"
          v-on:detailClicked="openModal"
        ></Card>
        <Card
          cardName="MTLOL QT"
          bgImg="image/smn.png"
          animationDelay="6.5"
          lodeStone="1569569"
          v-on:detailClicked="openModal"
        ></Card>
        <Card
          cardName="CLEES WHEATBUNS"
          bgImg="image/blu.png"
          profilePic="https://cdn.discordapp.com/avatars/49356348332179456/aada38e9e61fa1b76cff5ecbfd29598f.webp?size=128"
          twitterSrc="https://twitter.com/cleeeees"
          twitchSrc="https://www.twitch.tv/clees"
          youtubeSrc="https://www.youtube.com/c/Clees/"
          animationDelay="7"
          lodeStone="6623189"
          v-on:detailClicked="openModal"
        ></Card>
        <Card
          cardName="CLEES WHEATBUNS"
          bgImg="https://img2.finalfantasyxiv.com/f/a7f145e03053f4f44ec0ca8d0349edce_b937560c841465f7c4bc8eb47ea7948afl0_640x873.jpg?1633448153"
          profilePic="https://cdn.discordapp.com/avatars/49356348332179456/aada38e9e61fa1b76cff5ecbfd29598f.webp?size=128"
          twitterSrc="https://twitter.com/cleeeees"
          twitchSrc="https://www.twitch.tv/clees"
          youtubeSrc="https://www.youtube.com/c/Clees/"
          animationDelay="7"
          lodeStone="6623189"
          v-on:detailClicked="openModal"
        ></Card>
        <div
          class="flex animate-fade-in-up w-40 shadow-xl border-4 bg-transparent filter grayscale hover:filter-reset border-green-700 cursor-pointer"
          style="height: 500px;"
          @click="newCard = !newCard"
        >
          <PlusCircleIcon class="h-20 w-20 text-green-700 self-center mx-auto"></PlusCircleIcon>
        </div>
      </div>
    </video-background>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { ref } from "vue";
import { PlusCircleIcon } from '@heroicons/vue/outline'
import {
  TransitionRoot,
  TransitionChild,
  Dialog,
  DialogOverlay,
  DialogTitle,
  DialogDescription,
} from "@headlessui/vue";
import VideoBackground from 'vue-responsive-video-background-player';
import Card from './components/Card.vue';
export default defineComponent({
  name: 'App',
  components: {
    VideoBackground, TransitionChild, Card, Dialog, DialogOverlay, DialogTitle, DialogDescription, TransitionRoot, PlusCircleIcon
  },
  data() {
    return {
      title: "World First Racer",
      teamTag: "TPS",
      teamName: "Thoughts Per Second",
      videoBackground: {
        src: "vids/endwalkerLogin.mp4",
        muted: true,
        loop: false
      },
    }
  },
  setup() {
    // The open/closed state lives outside of the Dialog and
    // is managed by you.
    let isOpen = ref(false);
    let charDataloading = ref(false);
    let charData = ref();
    let newCard = ref(false);

    return {
      isOpen,
      charDataloading,
      charData,
      newCard,
      closeModal() {
        isOpen.value = false
      },
      async openModal(lodestone: any) {
        isOpen.value = true;
        charDataloading.value = true;
        const response = await fetch('https://xivapi.com/character/' + lodestone + '?extended=1');
        charData.value = await response.json();
        charDataloading.value = false;
      },
    };
  },
  methods: {
  }
});
</script>

<style>
.title {
  color: #e6e4e4;
  text-shadow: -0.1em -0.1em 0.1em #8d4909;
}
</style>