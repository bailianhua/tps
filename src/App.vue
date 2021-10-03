<template>
  <div class="app overflow-y-auto">
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
          modalImage="https://ffxiv-character-cards.herokuapp.com/characters/id/6455202.png"
        ></Card>
        <Card
          cardName="SINDALF SINDALF"
          bgImg="image/drk.png"
          profilePic="https://pbs.twimg.com/profile_images/1188497791275847680/-DrQVbly_400x400.jpg"
          twitterSrc="https://twitter.com/Sindalf"
          animationDelay="3.5"
          modalImage="https://ffxiv-character-cards.herokuapp.com/characters/id/1583960.png"
        ></Card>
        <Card
          cardName="KIONA LYNEAR"
          bgImg="image/whm.png"
          profilePic="https://cdn.discordapp.com/avatars/49249729237745664/acf02ccf4304a8706e1dac4af5ce455e.webp?size=128"
          twitterSrc="https://twitter.com/_Kionu_"
          youtubeSrc="https://www.youtube.com/user/xkadinx"
          animationDelay="4"
          modalImage="https://ffxiv-character-cards.herokuapp.com/characters/id/2500630.png"
        ></Card>
        <Card
          cardName="ARA HOSHIZORA"
          bgImg="image/ast.png"
          profilePic="https://pbs.twimg.com/profile_images/1349807474031939587/gn7WB6FM_400x400.jpg"
          twitterSrc="https://twitter.com/Ara_Hoshizora"
          animationDelay="4.5"
          modalImage="https://ffxiv-character-cards.herokuapp.com/characters/id/1826381.png"
        ></Card>
        <Card
          cardName="SHINA FLOREM"
          bgImg="image/nin.png"
          profilePic="https://pbs.twimg.com/profile_images/906667510971359232/vyy8dj7V_400x400.jpg"
          twitterSrc="https://twitter.com/yomikadoneko"
          animationDelay="5"
          modalImage="https://ffxiv-character-cards.herokuapp.com/characters/id/8856251.png"
        ></Card>
        <Card
          cardName="PHANTOM ASSASSIN"
          bgImg="image/brd.png"
          profilePic="https://pbs.twimg.com/profile_images/1277703728078950400/W5Oc5BIk_400x400.png"
          twitterSrc="https://twitter.com/Phantom_xiv"
          animationDelay="5.5"
          modalImage="https://ffxiv-character-cards.herokuapp.com/characters/id/8014568.png"
        ></Card>
        <Card
          cardName="SFIA PIRION"
          bgImg="image/blm.png"
          profilePic="https://pbs.twimg.com/profile_images/1196157469178744832/6RDSD2-P_400x400.jpg"
          twitterSrc="https://twitter.com/FFsfia"
          twitchSrc="https://www.twitch.tv/sfia"
          youtubeSrc="https://www.youtube.com/channel/UC5hfA-E66fLH9HVD5vuMdbQ"
          animationDelay="6"
          modalImage="https://ffxiv-character-cards.herokuapp.com/characters/id/1549390.png"
        ></Card>
        <Card
          cardName="MTLOL QT"
          bgImg="image/smn.png"
          animationDelay="6.5"
          modalImage="https://ffxiv-character-cards.herokuapp.com/characters/id/1569569.png"
        ></Card>
        <Card
          cardName="CLEES WHEATBUNS"
          bgImg="image/blu.png"
          profilePic="https://cdn.discordapp.com/avatars/49356348332179456/aada38e9e61fa1b76cff5ecbfd29598f.webp?size=128"
          twitterSrc="https://twitter.com/cleeeees"
          twitchSrc="https://www.twitch.tv/clees"
          youtubeSrc="https://www.youtube.com/c/Clees/"
          animationDelay="7"
          modalImage="https://ffxiv-character-cards.herokuapp.com/characters/id/6623189.png"
        ></Card>
        <Modal
          title="cardName"
          image="https://ffxiv-character-cards.herokuapp.com/characters/id/1549390.png"
        ></Modal>
      </div>
    </video-background>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import VideoBackground from 'vue-responsive-video-background-player';
import Card from './components/Card.vue';
import Modal from './components/Modal.vue';
export default defineComponent({
  name: 'App',
  components: { VideoBackground, Card, Modal },
  data() {
    return {
      title: "World First Racer",
      teamTag: "TPS",
      teamName: "Thoughts Per Second",
      videoBackground: {
        src: "/vids/endwalkerLogin.mp4",
        muted: true,
        loop: false
      }
    }
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