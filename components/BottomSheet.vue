<template>
  <div 
    class="fixed inset-x-0 bottom-0 transform transition-transform duration-300 ease-in-out"
    :class="{ 'translate-y-full': !isVisible }"
  >
    <div class="bg-white rounded-t-2xl p-8 min-h-[60vh] relative">
      <h2 class="text-[#1E1B4B] text-3xl font-bold mb-4">Ready to get started?</h2>
      <p class="text-gray-600 mb-8">Enter your number to help us set up your investment account.</p>

      <div class="flex gap-4 mb-8">
        <div class="bg-gray-100 px-4 py-3 rounded-lg">
          <span class="text-gray-700">+91</span>
        </div>
        <input 
          type="tel" 
          v-model="phoneNumber"
          class="flex-1 bg-gray-100 px-4 py-3 rounded-lg focus:outline-none"
          placeholder="Enter phone number"
        />
      </div>

      <div class="flex items-center gap-3 mb-12">
        <div 
          class="w-6 h-6 rounded-md bg-green-500 flex items-center justify-center cursor-pointer"
          @click="toggleWhatsApp"
        >
          <svg v-if="whatsAppEnabled" xmlns="http://www.w3.org/2000/svg" class="h-4 w-4 text-white" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd" />
          </svg>
        </div>
        <span class="text-gray-600">Enable WhatsApp notifications</span>
      </div>

      <p class="text-center text-gray-500 text-sm mb-8">
        By proceeding, you accept Ventura's 
        <a href="#" class="text-[#1E1B4B]">Terms of Use</a> and 
        <a href="#" class="text-[#1E1B4B]">Privacy Policy</a>
      </p>

      <button 
        @click="handleContinue"
        class="w-full bg-[#1E1B4B] text-white py-4 rounded-lg font-medium"
      >
        Continue
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
 import { ref, onMounted } from 'vue';

// const isVisible = ref(false);
// const phoneNumber = ref('');  // Initialize with an empty string
const whatsAppEnabled = ref(true);

const toggleWhatsApp = () => {
  whatsAppEnabled.value = !whatsAppEnabled.value;
};

const handleContinue = () => {
  // Handle continue action
  console.log('Continue with:', { phoneNumber: phoneNumber.value, whatsAppEnabled: whatsAppEnabled.value });
};

onMounted(() => {
  setTimeout(() => {
    isVisible.value = true;  // Corrected typo
  }, 1000);
});
</script>
