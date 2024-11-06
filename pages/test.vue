<template>
  <div class="min-h-screen bg-[#ECE8FF] relative overflow-hidden font-inter">
    <div class="fixed inset-0 bg-orange-500 z-40" v-if="isOpen" @click="closeBottomSheet">
      <div class="flex justify-between">
        <div></div>
        <div class="p-7 text-xl text-white font-bold font-serif">ventura</div>
      </div>
    </div>
    <div class="fixed h-[90%] bottom-0 left-0 right-0 bg-white z-50 transition-transform transform rounded-t-xl" :class="{ 'translate-y-0': isOpen, 'translate-y-full': !isOpen }">
      <div class="md:w-[40%] md:flex md:mx-auto md:justify-center md:items-center">
        <div v-if="verificationStep">
          <div class="md:pt-5 sm:pt-10 pb-5 relative">
            <div class="rounded-lg px-2">
              <div class="flex flex-col">
                <!-- Steps for e-KYC -->
                <button class="bg-[#1E1B4B] text-white py-2 px-4 rounded-lg w-full" @click="handleContinue">
                  Open camera
                </button>
              </div>
            </div>
          </div>
        </div>
        <div v-if="isCameraAccess">
          <div class="p-6 rounded-lg md:my-6">
            <h1 class="text-xl font-bold text-[#1f1f1f] mb-2">Take a Selfie</h1>
            <div class="bg-[#f3f4f6] p-4 rounded-lg mb-4">
              <div class="relative">
                <video ref="videoElement" class="w-full h-auto rounded-lg" autoplay playsinline></video>
                <button @click="capture" class="absolute bottom-5 left-1/2 transform -translate-x-1/2 bg-blue-500 text-white px-6 py-2 rounded-full shadow-md hover:bg-blue-600 transition duration-200">
                  Capture
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from "vue";

const videoElement = ref<HTMLVideoElement | null>(null);
const isOpen = ref(false);
const verificationStep = ref(true);
const isCameraAccess = ref(false);
const cameraaccessdialog = ref(false);
const hasPermissions = ref(false);

const openBottomSheet = () => {
  isOpen.value = true;
};

const closeBottomSheet = () => {
  isOpen.value = false;
};

onMounted(() => {
  setTimeout(openBottomSheet, 100);
});

const nextStep = () => {
  verificationStep.value = false;
  isCameraAccess.value = true;
};

const handleConfirm = async () => {
  try {
    const stream = await navigator.mediaDevices.getUserMedia({ video: true });
    hasPermissions.value = true;
    startCamera(stream);
  } catch (error) {
    console.error("Error requesting permissions:", error);
    alert('Unable to access the camera. Please check your permissions.');
  }
};

const startCamera = (stream: MediaStream) => {
  if (videoElement.value) {
    videoElement.value.srcObject = stream;
  }
  
  onUnmounted(() => {
    const tracks = stream.getTracks();
    tracks.forEach(track => track.stop());
  });
};

const handleContinue = () => {
  if (hasPermissions.value) {
    isCameraAccess.value = true;
    handleConfirm(); // Request camera access
  } else {
    cameraaccessdialog.value = true;
  }
};
</script>

<style scoped lang="scss">
video {
  object-fit: cover;
}
</style>