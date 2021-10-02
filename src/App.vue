<template>
  <div class="app">
    <video-background
      :src="videoBackground.src"
      :muted="videoBackground.muted"
      :loop="videoBackground.loop"
      style="height: 100vh;"
      overlay="rgba(50, 50, 50, 0.7)"
    >
      <p
        class="underline align-middle text-gray-100 text-center text-5xl tracking-tight"
      >{{ title }}</p>
      <p
        class="align-middle text-gray-100 text-center text-5xl font-black tracking-widest leading-relaxed"
      >{{ teamTag }}</p>
      <p
        class="italic align-middle text-gray-100 text-center text-2xl font-bold tracking-tight"
      >{{ teamName }}</p>
    </video-background>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import VideoBackground from 'vue-responsive-video-background-player';
export default defineComponent({
  name: 'App',
  components: { VideoBackground },
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
  }
});
</script>

<style>
.title {
  color: #e6e4e4;
  text-shadow: -0.1em -0.1em 0.1em #8d4909;
}
</style>