<template>
  <div class="h-screen bg-[#ECE8FF] relative overflow-hidden font-inter">
    <div class="fixed inset-0 bg-primary z-40" v-if="isOpen">
      <div class="flex justify-between">
        <div></div>
        <div class="p-7 text-xl text-white font-bold font-serif">goodwill</div>
      </div>
    </div>
  <div
    class="fixed h-[90%] bottom-0 left-0 right-0 bg-white z-50 transition-transform transform rounded-t-xl"
    :class="{ 'translate-y-0': isOpen, 'translate-y-full': !isOpen }"
  >
    <div class="md:w-[40%] md:mx-auto px-4 relative h-full pb-20">
      <div class="md:pt-5 sm:pt-10 pb-5 relative max-w-md mx-auto">
      
        <h1 class="text-2xl font-semibold text-bigtext mb-1">
              Enter your PAN
            </h1>
        <div class="my-1">
            <label
                  for="name"
                  class="block text-sm font-medium text-bigtext mb-1"
                  >ADHAR</label
                >
          <FileUpload 
            @file-selected="handleFileSelected"
            @file-removed="handleFileRemoved"
          />
        </div>
         <div class="my-1">
            <label
                  for="name"
                  class="block text-sm font-medium text-bigtext mb-1"
                  >PAN</label
                >
          <FileUpload 
            @file-selected="handleFileSelected"
            @file-removed="handleFileRemoved"
          />
        </div>
         <div class="my-1">
            <label
                  for="name"
                  class="block text-sm font-medium text-bigtext mb-1"
                  >EDUCATION PROOF</label
                >
          <FileUpload 
            @file-selected="handleFileSelected"
            @file-removed="handleFileRemoved"
          />
        </div>
      </div>
      
      <!-- Fixed width container for button -->
      <div class="fixed bottom-0 left-0 right-0 p-4 bg-white">
        <div class="md:w-[40%] md:mx-auto">
          <button
            type="submit"
            class="w-full bg-[#1E1B4B] text-white rounded-lg py-3 font-medium transition-colors hover:bg-[#2d2974] disabled:cursor-not-allowed"
            :disabled="!hasFile"
            @click="nextStep"
          >
            Continue
          </button>
        </div>
      </div>
    </div>
  </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

import FileUpload from '@/components/FileUpload.vue';
const isOpen = ref(true);
const hasFile = ref(false);

const handleFileSelected = (file: File) => {
  hasFile.value = true;
};

const handleFileRemoved = () => {
  hasFile.value = false;
};

const nextStep = () => {
  // Handle next step logic
  console.log('Next step clicked');
};
</script>