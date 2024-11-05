<template>
  <div v-if="showTruecaller" class="md:my-10 sm:my-20 md:mx-20">
    <div>
      <!-- Content -->
      <div class="p-8 rounded-2xl md:shadow-2xl overflow-hidden bg-white">
        <div class="grid grid-cols-2 py-4 ">
          <img
            src="public/images/venturalogo.jpeg"
            alt="Google"
            class="w-45 h-14"
          />
          <!-- <div class=" inset-0 grid grid-cols-6 w-[100px] p-0 ">
      <div v-for="i in 36" :key="i" class="border border-[rgba(72,52,129,0.1)]"></div>
    </div> -->
        </div>
        <h1 class="text-gray-600 text-2xl font-bold mb-4 pl-1 ">
          Enter OTP here
        </h1>
        <p class="text-gray-600 mb-8 pl-1">
          We have sent an OTP to your mobile number<br />
          +91 *****{{ phoneNumber.slice(-4) }}
        </p>

        <!-- OTP Input -->
        <div class="flex gap-2 mb-8 mr-3">
          <template v-for="(digit, index) in 6" :key="index">
            <input
              type="text"
              maxlength="1"
              v-model="otpDigits[index]"
              @input="handleOtpInput($event, index)"
              @keydown.delete="handleBackspace($event, index)"
              @keydown.left="focusPrevInput(index)"
              @keydown.right="focusNextInput(index)"
              class="md:w-[50px] md:h-[50px] sm:w-[40px] sm:h-[40px]  border-2 border-gray-200 rounded-lg text-center text-xl font-semibold focus:border-[#1E1B4B] focus:outline-none"
              :ref="(el) => (inputRefs[index] = el)"
            />
          </template>
        </div>

        <!-- Timer -->
        <div class="flex justify-between items-center mb-12">
          <p class="text-gray-600">{{ formatTime(timer) }}</p>
          <button
            @click="resendOtp"
            :disabled="timer > 0"
            :class="timer > 0 ? 'text-gray-400' : 'text-red-500'"
            class="font-medium"
          >
            Resend OTP
          </button>
        </div>

        <!-- Verify Button -->
        <button
          @click="verifyOtp"
          :disabled="!isOtpComplete"
          class="w-full py-4 rounded-lg font-medium transition-colors"
          :class="
            isOtpComplete
              ? 'bg-[#1E1B4B] text-white'
              : 'bg-gray-200 text-gray-500'
          "
        >
          Verify OTP
        </button>
      </div>
    </div>
  </div>
  <div v-else-if="showEmailOtp" class="md:my-10 sm:my-20  md:mx-20">
    <div>
      <!-- Content -->
      <div class="p-8 rounded-2xl md:shadow-2xl overflow-hidden bg-white">
        <div class="grid grid-cols-2 py-3">
          <img
            src="public/images/venturalogo.jpeg"
            alt="Google"
            class="w-45 h-14"
          />
          <!-- <div class=" inset-0 grid grid-cols-6 w-[100px] p-0 ">
      <div v-for="i in 36" :key="i" class="border border-[rgba(72,52,129,0.1)]"></div>
    </div> -->
        </div>
        <h1 class="text-gray-600 text-2xl font-bold mb-4 pl-1">
          Enter OTP here
        </h1>
        <p class="text-gray-600 mb-8 pl-1">
          We have sent an OTP to your email id <br />
         ******@gmail.com
        </p>

        <!-- OTP Input -->
        <div class="flex gap-2 mb-8 mr-3">
          <template v-for="(digit, index) in 6" :key="index">
            <input
              type="text"
              maxlength="1"
              v-model="otpDigits1[index]"
              @input="handleOtpInput1($event, index)"
              @keydown.delete="handleBackspace1($event, index)"
              @keydown.left="focusPrevInput1(index)"
              @keydown.right="focusNextInput1(index)"
              class="md:w-[50px] md:h-[50px] sm:w-[40px] sm:h-[40px]  border-2 border-gray-200 rounded-lg text-center text-xl font-semibold focus:border-[#1E1B4B] focus:outline-none"
              :ref="(el) => (inputRefs1[index] = el)"
            />
          </template>
        </div>

        <!-- Timer -->
        <div class="flex justify-between items-center mb-12">
          <p class="text-gray-600">{{ formatTime(timer) }}</p>
          <button
            @click="resendOtp"
            :disabled="timer > 0"
            :class="timer > 0 ? 'text-gray-400' : 'text-red-500'"
            class="font-medium"
          >
            Resend OTP
          </button>
        </div>

        <!-- Verify Button -->
        <button
          @click="verifyOtpforEmail"
          :disabled="!isOtpComplete1"
          class="w-full py-4 rounded-lg font-medium transition-colors"
          :class="
            isOtpComplete1
              ? 'bg-[#1E1B4B] text-white'
              : 'bg-gray-200 text-gray-500'
          "
        >
          Verify OTP
        </button>
      </div>
    </div>
  </div>
  <div v-else-if="EmailHandling" class="md:my-10 md:mx-20">
    <div class="bg-white rounded-t-2xl p-10 md:shadow-2xl">
      <div class="flex flex-col mt-10 mx-1">
        <div class="grid grid-cols-2 py-3">
          <img
            src="public/images/venturalogo.jpeg"
            alt="Google"
            class="w-45 h-14"
          />
          <!-- <div class=" inset-0 grid grid-cols-6 w-[100px] p-0 ">
      <div v-for="i in 36" :key="i" class="border border-[rgba(72,52,129,0.1)]"></div>
    </div> -->
        </div>
        <h2 class="text-2xl font-bold mb-4 pl-1 text-gray-600">
          Add your email
        </h2>
        <p class="text-gray-600 mb-6 pl-1">
          This is where we'll send you important updates and insights on the
          market.
        </p>
        <input
          v-model="email"
          type="email"
          placeholder="Enter email"
          class="w-full px-4 py-3 rounded-md border border-gray-300 focus:outline-none focus:border-[#1E1B4B] mb-6"
        />
        <button
          @click="handleDone(email)"
          :disabled="!email"
          class="w-full py-3 rounded-lg font-medium transition-colors"
          :class="
            isValidEmail(email)
              ? 'bg-[#1E1B4B] text-white'
              : 'bg-gray-200 text-gray-500'
          "
        >
          Verify email
        </button>
        <p class="text-gray-600 mt-2 text-center">or</p>
        <button
          @click="openVerifygoogle = true"
          class="bg-[#1A1442] text-white py-2 px-4 inline-flex items-center justify-center focus:outline-none focus:shadow-outline mt-4 w-full rounded-lg font-medium transition-colors"
        >
          <img
            src="public/images/google-Photoroom.png"
            alt="Google"
            class="w-8 h-8 mx-3"
          />
          <span>Continue with Google</span>
        </button>
      </div>
    </div>
  </div>
  <div class="md:my-10 md:mx-20" v-else>
    <div class="bg-white rounded-2xl p-10 md:shadow-2xl">
      <div class="grid grid-cols-2 py-3">
        <img
          src="public/images/venturalogo.jpeg"
          alt="Google"
          class="w-45 h-14"
        />
        <!-- <div class=" inset-0 grid grid-cols-6 w-[100px] p-0 ">
      <div v-for="i in 36" :key="i" class="border border-[rgba(72,52,129,0.1)]"></div>
    </div> -->
      </div>

      <h2 class="text-gray-600 text-3xl font-bold mb-4 pl-1">
        Ready to get started?
      </h2>
      <p class="text-gray-600 mb-8 pl-1">
        Enter your number to help us set up your investment account.
      </p>

      <div class="flex gap-4 mb-8">
        <div class="bg-gray-100 px-4 py-3 rounded-lg">
          <span class="text-gray-700">+91</span>
        </div>
        <input
          type="tel"
          v-model="phoneNumber"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg  focus:border-[#1E1B4B] block w-full p-2.5"
          placeholder="Enter phone number"
          required
        />
      </div>

      <div class="flex items-center gap-3 mb-2">
        <button
          class="w-6 h-6 rounded-md flex items-center justify-center cursor-pointer"
          :class="whatsAppEnabled ? 'bg-green-500' : 'bg-gray-200'"
          @click="toggleWhatsApp"
        >
          <svg
            v-if="whatsAppEnabled"
            xmlns="http://www.w3.org/2000/svg"
            class="h-4 w-4 text-white"
            viewBox="0 0 20 20"
            fill="currentColor"
          >
            <path
              fill-rule="evenodd"
              d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
              clip-rule="evenodd"
            />
          </svg>
        </button>
        <span class="text-gray-600">Enable WhatsApp notifications</span>
      </div>
      <p class="text-center text-gray-900 font-semibold text-sm py-4">
        Have an account ?
        <span class="text-[#FF7F50] font-semibold">Login</span>
      </p>
      <p class="text-center text-gray-500 text-sm mb-8">
        By proceeding, you accept Ventura's
        <a href="#" class="text-[#1E1B4B] font-semibold">Terms of Use</a> and
        <a href="#" class="text-[#1E1B4B] font-semibold">Privacy Policy</a>
      </p>

      <button
        @click="handleContinue"
        class="w-full bg-[#1E1B4B] text-white py-4 rounded-lg font-medium"
        :disabled="!phoneNumber && phoneNumber.length != 10"
        :class="
          phoneNumber && phoneNumber.length == 10
            ? 'bg-[#1E1B4B] text-white'
            : 'bg-gray-200 text-gray-500'
        "
      >
        Continue
      </button>
    </div>
  </div>
  <div
    class="relative z-10"
    aria-labelledby="modal-title"
    role="dialog"
    aria-modal="true"
  >
    <!--
    Background backdrop, show/hide based on modal state.

    Entering: "ease-out duration-300"
      From: "opacity-0"
      To: "opacity-100"
    Leaving: "ease-in duration-200"
      From: "opacity-100"
      To: "opacity-0"
  -->
    <div
      class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity"
      aria-hidden="true"
      v-if="openVerifygoogle"
    ></div>

    <div
      v-if="openVerifygoogle"
      class="fixed inset-0 z-10 w-screen overflow-y-auto"
    >
      <div
        class="flex min-h-full items-center justify-center p-4 text-center sm:items-center sm:p-0"
      >
        <!--
        Modal panel, show/hide based on modal state.

        Entering: "ease-out duration-300"
          From: "opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
          To: "opacity-100 translate-y-0 sm:scale-100"
        Leaving: "ease-in duration-200"
          From: "opacity-100 translate-y-0 sm:scale-100"
          To: "opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
      -->
        <div
          class="relative transform overflow-hidden rounded-lg bg-white text-left shadow-xl transition-all sm:my-8 sm:w-full sm:max-w-lg"
        >
          <div class="bg-white rounded-lg p-5 shadow-lg h-[400px]">
            <div class="flex justify-center items-center">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke="red"
                className="size-6"
                class="h-20 w-20 mt-10"
              >
                <path
                  strokeLinecap="round"
                  strokeLinejoin="round"
                  d="m11.25 11.25.041-.02a.75.75 0 0 1 1.063.852l-.708 2.836a.75.75 0 0 0 1.063.853l.041-.021M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Zm-9-3.75h.008v.008H12V8.25Z"
                />
              </svg>
            </div>
            <div
              class="text-2xl font-bold py-3 flex justify-center items-center"
            >
              Gmail Verification Failed
            </div>
            <p class="text-md flex justify-center items-center">
              There was an error when completing this step
            </p>
            <div class="flex justify-center items-center py-4">
              <button
                @click="closeSheet"
                class="mt-4 bg-[#1E1B4B] text-white px-4 py-2 rounded"
              >
                Try Again
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref, onMounted } from "vue";

import TruecallerVerification from "./TrueCallerVerification.vue";
import { useRouter } from 'vue-router';

const router = useRouter();
const showPostVerification = ref(false);
const isVisible = ref(false);
const showTruecaller = ref(false);
const EmailHandling = ref(false);
const phoneNumber = ref("");
const whatsAppEnabled = ref(true);

const toggleWhatsApp = () => {
  whatsAppEnabled.value = !whatsAppEnabled.value;
};
const email = ref("");
const closeBottomSheet = () => {
  isVisible.value = false;
};
function isValidEmail(email: string): boolean {
  // Regular expression for validating an email
  const emailRegex: RegExp = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;

  // Test the email against the regex
  return emailRegex.test(email);
}
const handleDone = (email: any) => {
  let val = isValidEmail(email);
  if (val) {
    showEmailOtp.value=true
  } else {
    console.log("error");
  }
};
const handleContinue = () => {
  if (phoneNumber.value && phoneNumber.value.length == 10) {
    showTruecaller.value = true;
  }
};
const props = defineProps<{
  isVisible: boolean;
  phoneNumber: string;
}>();

const emit = defineEmits(["close", "verified"]);

const otpDigits = ref(["", "", "", "", "", ""]);
const otpDigits1 = ref(["", "", "", "", "", ""]);
const inputRefs = ref<HTMLInputElement[]>([]);
const inputRefs1 = ref<HTMLInputElement[]>([]);
const timer = ref(60);
const timer1 = ref(60);
let timerInterval: NodeJS.Timer | null = null;
const openVerifygoogle = ref(false);
const isOtpComplete = computed(() => {
  return otpDigits.value.every((digit) => digit !== "");
});
const isOtpComplete1 = computed(() => {
  return otpDigits1.value.every((digit) => digit !== "");
});
const showEmailOtp=ref(false)

const formatTime = (seconds: number) => {
  const mins = Math.floor(seconds / 60);
  const secs = seconds % 60;
  return `${String(mins).padStart(2, "0")}:${String(secs).padStart(2, "0")}s`;
};

const handleOtpInput = (event: Event, index: number) => {
  const input = event.target as HTMLInputElement;
  const value = input.value;

  // Ensure only numbers are entered
  if (!/^\d*$/.test(value)) {
    otpDigits.value[index] = "";
    return;
  }

  otpDigits.value[index] = value;

  // Move to next input if available
  if (value && index < 5) {
    inputRefs.value[index + 1]?.focus();
  }
};
const handleOtpInput1 = (event: Event, index: number) => {
  const input = event.target as HTMLInputElement;
  const value = input.value;

  // Ensure only numbers are entered
  if (!/^\d*$/.test(value)) {
    otpDigits1.value[index] = "";
    return;
  }

  otpDigits1.value[index] = value;

  // Move to next input if available
  if (value && index < 5) {
    inputRefs1.value[index + 1]?.focus();
  }
};
const handleBackspace = (event: KeyboardEvent, index: number) => {
  if (!otpDigits.value[index] && index > 0) {
    otpDigits.value[index - 1] = "";
    inputRefs.value[index - 1]?.focus();
  }
};
const handleBackspace1 = (event: KeyboardEvent, index: number) => {
  if (!otpDigits1.value[index] && index > 0) {
    otpDigits1.value[index - 1] = "";
    inputRefs1.value[index - 1]?.focus();
  }
};

const focusPrevInput = (index: number) => {
  if (index > 0) {
    inputRefs.value[index - 1]?.focus();
  }
};
const focusPrevInput1 = (index: number) => {
  if (index > 0) {
    inputRefs1.value[index - 1]?.focus();
  }
};
const focusNextInput1 = (index: number) => {
  if (index < 5) {
    inputRefs1.value[index + 1]?.focus();
  }
};
const focusNextInput = (index: number) => {
  if (index < 5) {
    inputRefs.value[index + 1]?.focus();
  }
};

const startTimer = () => {
  timer.value = 60;
  timerInterval = setInterval(() => {
    if (timer.value > 0) {
      timer.value--;
    } else {
      if (timerInterval) clearInterval(timerInterval);
    }
  }, 1000);
};
const startTimer1 = () => {
  timer1.value = 60;
  timerInterval = setInterval(() => {
    if (timer1.value > 0) {
      timer1.value--;
    } else {
      if (timerInterval) clearInterval(timerInterval);
    }
  }, 1000);
};

const resendOtp = () => {
  if (timer.value === 0) {
    // Reset OTP inputs
    otpDigits.value = ["", "", "", "", "", ""];
    // Restart timer
    startTimer();
    // TODO: Add API call to resend OTP
    console.log("Resending OTP...");
  }
};
const resendOtp1 = () => {
  if (timer1.value === 0) {
    // Reset OTP inputs
    otpDigits1.value = ["", "", "", "", "", ""];
    // Restart timer
    startTimer1();
    // TODO: Add API call to resend OTP
    console.log("Resending OTP...");
  }
};
const verifyOtp = () => {
  const otp = otpDigits.value.join("");
  console.log("Verifying OTP:", otp);
  showTruecaller.value = false;
  EmailHandling.value = true;
};
const verifyOtpforEmail = () =>{
     const otp = otpDigits.value.join("");
 router.push('/SecondStep');
}
const closeSheet = () => {
  openVerifygoogle.value = false;
};

onMounted(() => {
  startTimer();
    startTimer1();
});

onUnmounted(() => {
  if (timerInterval) clearInterval(timerInterval);
});
const closeTruecaller = () => {
  showTruecaller.value = false;
};

const handleVerified = () => {
  console.log("Verified with Truecaller");
  showTruecaller.value = false;
  isVisible.value = false;
  showPostVerification.value = true; // Show post-verification sheet
};

const closePostVerification = () => {
  showPostVerification.value = false; // Close post-verification sheet
};

const handleSkip = () => {
  console.log("Skipped Truecaller verification");
  showTruecaller.value = false;
};

onMounted(() => {
  setTimeout(() => {
    isVisible.value = true;
  }, 1000);
});
</script>