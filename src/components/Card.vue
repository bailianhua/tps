<template>
    <div
        class="hover:filter-reset filter grayscale rounded bg-cover bg-center w-40 h-full"
        :style="cardStyle"
    ></div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name: 'Card',
    components: {},
    data() {
        return {
            name: "Super Peasant",
            cardStyle: {
                backgroundImage: 'url("/image/blm.png")'
            }
        }
    }
}
);
</script>
<style>
</style>