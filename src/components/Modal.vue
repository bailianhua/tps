<template>
    <transition name="fade">
        <Dialog :open="isOpen" @close="setIsOpen">
            <DialogOverlay />

            <DialogTitle>Deactivate account</DialogTitle>
            <DialogDescription>This will permanently deactivate your account</DialogDescription>

            <p>
                Are you sure you want to deactivate your account? All of your data will be
                permanently removed. This action cannot be undone.
            </p>

            <button @click="setIsOpen(false)">Deactivate</button>
            <button @click="setIsOpen(false)">Cancel</button>
        </Dialog>
    </transition>
</template>
<script lang="ts">
import { ref } from "vue";
import {
    Dialog,
    DialogOverlay,
    DialogTitle,
    DialogDescription,
} from "@headlessui/vue";

export default {
    components: { Dialog, DialogOverlay, DialogTitle, DialogDescription },
    setup() {
        let isOpen = ref(true);

        return {
            isOpen,
            setIsOpen(value: any) {
                isOpen.value = value;
            },
        };
    },
};</script>
<style>
</style>