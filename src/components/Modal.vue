<template>
    <div
        class="modal opacity-0 pointer-events-none fixed w-full h-full top-0 left-0 flex items-center justify-center z-50"
    >
        <div class="modal-overlay absolute w-full h-full bg-gray-900 opacity-50"></div>

        <div
            class="modal-container w-11/12 md:max-w-md mx-auto rounded shadow-lg z-50 overflow-y-auto bg-yellow-50"
        >
            <!-- Add margin if you want to see some of the overlay behind the modal-->
            <div class="modal-content py-4 text-left px-6">
                <!--Title-->
                <div class="flex justify-between items-center pb-3">
                    <p
                        class="text-2xl font-bold"
                    >Working on dynamic modal but for now everyone is sfia</p>
                    <div class="modal-close cursor-pointer z-50">
                        <svg
                            class="fill-current text-black"
                            xmlns="http://www.w3.org/2000/svg"
                            width="18"
                            height="18"
                            viewBox="0 0 18 18"
                            v-on:click="toggleModal"
                        >
                            <path
                                d="M14.53 4.53l-1.06-1.06L9 7.94 4.53 3.47 3.47 4.53 7.94 9l-4.47 4.47 1.06 1.06L9 10.06l4.47 4.47 1.06-1.06L10.06 9z"
                            />
                        </svg>
                    </div>
                </div>

                <!--Body-->
                <img :src="image" class="w-full h-full rounded-md border-8 border-blue-100" />

                <!--Footer-->
                <div class="flex justify-center pt-2">
                    <button
                        class="modal-close px-4 bg-indigo-500 p-3 rounded-lg text-white hover:bg-indigo-400"
                        v-on:click="toggleModal"
                    >Close</button>
                </div>
            </div>
        </div>
    </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name: 'Modal',
    components: {},
    props: {
        'title': { Type: String, default: "" },
        'image': { Type: String, default: "" }
    },
    computed: {
    },
    data() {
        return {
        }
    },
    methods: {
        toggleModal: function () {
            const body = document.querySelector('body')
            const modal = document.querySelector('.modal');
            if (modal && body) {
                modal.classList.toggle('opacity-0')
                modal.classList.toggle('pointer-events-none')
                body.classList.toggle('modal-active')
            }
        }
    }
}
);</script>
<style>
</style>