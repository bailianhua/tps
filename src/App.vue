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
        class="underline align-middle text-gray-100 text-center text-5xl tracking-tight pt-5"
      >{{ title }}</p>
      <p
        class="align-middle text-gray-100 text-center text-5xl font-black tracking-widest leading-relaxed"
      >{{ teamTag }}</p>
      <p
        class="italic align-middle text-gray-100 text-center text-2xl font-bold tracking-tight"
      >{{ teamName }}</p>
      <div
        class="flex flex-wrap justify-center w-screen pt-10 overflow-y-auto gap-x-10 gap-y-5"
        style="height: 555px"
      >
        <Card></Card>
        <Card></Card>
        <Card></Card>
        <Card></Card>
        <Card></Card>
        <Card></Card>
        <Card></Card>
        <Card></Card>
        <Card></Card>
      </div>
    </video-background>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import VideoBackground from 'vue-responsive-video-background-player';
import Card from './components/Card.vue';
export default defineComponent({
  name: 'App',
  components: { VideoBackground, Card },
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