<template>
  <div class="min-h-screen bg-[#ECE8FF] relative overflow-hidden font-inter">
    <div
      class="fixed inset-0 bg-[#FF844B] z-40"
      v-if="isOpen"
      @click="closeBottomSheet"
    >
      <div class="flex justify-between">
        <div></div>
        <div class="p-7 text-xl text-white font-bold font-serif">ventura</div>
      </div>
    </div>
    <div
      class="fixed h-[90%] bottom-0 left-0 right-0 bg-white z-50 transition-transform transform rounded-t-xl"
      :class="{ 'translate-y-0': isOpen, 'translate-y-full': !isOpen }"
    >
      <div
        class="md:w-[40%] md:flex md:mx-auto md:justify-center md:items-center"
      >
        <!-- <div class="absolute inset-0 grid grid-cols-12 h-[300px]">
        <div v-for="i in 48" :key="i" class="border border-[#dad3fc]"></div>
      </div> -->
        <div v-if="verificationStep">
          <div class="md:pt-5 sm:pt-10 pb-5 relative">
            <!-- <div class="flex items-center justify-center text-center">
          <img
            src="public/images/ventura.jpeg"
            alt="Google"
            class="w-30 h-30"
          />
        </div> -->

            <div class="rounded-lg px-2">
              <div class="flex flex-col">
                <div class="flex items-center align-center space-x-10">
                  <div class="bg-green-200 rounded-full p-3">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24"
                      fill="green"
                      class="h-5 w-5"
                    >
                      <path
                        fill-rule="evenodd"
                        d="M19.916 4.626a.75.75 0 0 1 .208 1.04l-9 13.5a.75.75 0 0 1-1.154.114l-6-6a.75.75 0 0 1 1.06-1.06l5.353 5.353 8.493-12.74a.75.75 0 0 1 1.04-.207Z"
                        clip-rule="evenodd"
                      />
                    </svg>
                  </div>

                  <div class="mb-4">
                     

                    <h3 class="text-md font-bold">Complete e-KYC</h3>
                    <p class="text-gray-600 text-sm">
                      Keep your Aadhaar and PAN card handy
                    </p>
                  </div>
                </div>

                <div class="flex items-center space-x-10">
                  <div class="bg-green-200 rounded-full p-3">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24"
                      fill="green"
                      class="h-5 w-5"
                    >
                      <path
                        fill-rule="evenodd"
                        d="M19.916 4.626a.75.75 0 0 1 .208 1.04l-9 13.5a.75.75 0 0 1-1.154.114l-6-6a.75.75 0 0 1 1.06-1.06l5.353 5.353 8.493-12.74a.75.75 0 0 1 1.04-.207Z"
                        clip-rule="evenodd"
                      />
                    </svg>
                  </div>
                  <div class="mb-3">
                     

                    <div class="text-md font-bold">Setup Your Profile</div>
                    <div class="text-gray-600 text-sm">
                      Answer a few question about yourself
                    </div>
                  </div>
                </div>
                <div class="font-bold text-2xl py-3 px-1">Next Up...</div>
                <div class="flex items-center space-x-10">
                  <div class="bg-purple-200 rounded-full p-3">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      class="w-4 h-4 text-gray-500"
                      fill="none"
                      viewBox="0 0 24 24"
                      stroke-width="1.5"
                      stroke="currentColor"
                    >
                      <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        d="M15.75 6a3.75 3.75 0 1 1-7.5 0 3.75 3.75 0 0 1 7.5 0ZM4.501 20.118a7.5 7.5 0 0 1 14.998 0A17.933 17.933 0 0 1 12 21.75c-2.676 0-5.216-.584-7.499-1.632Z"
                      />
                    </svg>
                  </div>
                  <div class="mb-3">
                     

                    <h3 class="text-md font-bold">Link your bank a/c</h3>
                    <p class="text-gray-600 text-sm">
                      Set the primary account for your transaction
                    </p>
                  </div>
                </div>
                <div class="flex items-center space-x-10">
                  <div class="bg-purple-200 rounded-full p-3">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      class="w-4 h-4 text-gray-500"
                      fill="none"
                      viewBox="0 0 24 24"
                      stroke-width="1.5"
                      stroke="currentColor"
                    >
                      <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        d="M11.35 3.836c-.065.21-.1.433-.1.664 0 .414.336.75.75.75h4.5a.75.75 0 0 0 .75-.75 2.25 2.25 0 0 0-.1-.664m-5.8 0A2.251 2.251 0 0 1 13.5 2.25H15c1.012 0 1.867.668 2.15 1.586m-5.8 0c-.376.023-.75.05-1.124.08C9.095 4.01 8.25 4.973 8.25 6.108V8.25m8.9-4.414c.376.023.75.05 1.124.08 1.131.094 1.976 1.057 1.976 2.192V16.5A2.25 2.25 0 0 1 18 18.75h-2.25m-7.5-10.5H4.875c-.621 0-1.125.504-1.125 1.125v11.25c0 .621.504 1.125 1.125 1.125h9.75c.621 0 1.125-.504 1.125-1.125V18.75m-7.5-10.5h6.375c.621 0 1.125.504 1.125 1.125v9.375m-8.25-3 1.5 1.5 3-3.75"
                      />
                    </svg>
                  </div>
                  <div class="mb-3">
                     

                    <h3 class="text-md font-bold">Confirm it's you</h3>
                    <p class="text-gray-600 text-sm">
                      Click a photo and submit your signature
                    </p>
                  </div>
                </div>
                <div class="flex items-center space-x-10">
                  <div class="bg-purple-200 rounded-full p-3">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24"
                      fill="currentColor"
                      class="w-4 h-4 text-gray-500"
                    >
                      <path
                        d="M21.731 2.269a2.625 2.625 0 0 0-3.712 0l-1.157 1.157 3.712 3.712 1.157-1.157a2.625 2.625 0 0 0 0-3.712ZM19.513 8.199l-3.712-3.712-8.4 8.4a5.25 5.25 0 0 0-1.32 2.214l-.8 2.685a.75.75 0 0 0 .933.933l2.685-.8a5.25 5.25 0 0 0 2.214-1.32l8.4-8.4Z"
                      />
                      <path
                        d="M5.25 5.25a3 3 0 0 0-3 3v10.5a3 3 0 0 0 3 3h10.5a3 3 0 0 0 3-3V13.5a.75.75 0 0 0-1.5 0v5.25a1.5 1.5 0 0 1-1.5 1.5H5.25a1.5 1.5 0 0 1-1.5-1.5V8.25a1.5 1.5 0 0 1 1.5-1.5h5.25a.75.75 0 0 0 0-1.5H5.25Z"
                      />
                    </svg>
                  </div>
                  <div class="mb-3">
                     

                    <h3 class="text-md font-bold">eSign Ang Login</h3>
                    <p class="text-gray-600 text-sm">
                      Sign your Application and start Investing
                    </p>
                  </div>
                </div>

                <button
                  class="bg-[#1E1B4B] animate-bounce text-white font-bold py-3 mb-3 px-2 md:w-[30%] sm:w-[95%] fixed bottom-0 rounded-lg mt-8"
                  @click="nextStep"
                >
                  Continue
                </button>
              </div>
            </div>
          </div>
        </div>
        <div v-if="bankVerification">
          <div class="max-w-2xl mx-auto md:p-8 sm:py-8 sm:px-3">
            <h1 class="text-2xl font-semibold mb-2">Add bank account</h1>
            <p class="text-gray-600 mb-4">
              This will be your primary account for all transactions.
            </p>
            <div class="bg-green-100 text-green-700 p-4 rounded mb-4">
              <i class="fas fa-lock"></i> Your bank details are secured and will
              not be shared with anyone
            </div>
            <div class="relative mb-6">
              <input
                v-model="searchQuery"
                class="w-full p-3 border rounded focus:outline-none focus:ring-2 focus:ring-[#1E1B4B]"
                placeholder="Search your Bank"
                type="text"
              />
              <i class="fas fa-search absolute right-3 top-3 text-gray-400"></i>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-2">
              <div>
                <h2 class="text-gray-600 mb-2">POPULAR BANKS</h2>
                <div class="bg-gray-100 px-1 rounded flex space-x-2">
                  <div
                    v-for="bank in filteredPopularBanks"
                    :key="bank.name"
                    class="flex flex-col items-center text-center rounded-md p-2 my-1 hover:bg-[#1E1B4B] hover:text-white"
                    @click="setBankAccount(bank.name)"
                    :class="{
                      'bg-[#1E1B4B] text-white':
                        selectedBankAccount === bank.name,
                      'bg-gray-100': selectedBankAccount !== bank.name,
                    }"
                  >
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24"
                      :fill="
                        selectedBankAccount === bank.name ? 'white' : '#1E1B4B'
                      "
                      class="h-5 w-5"
                    >
                      <path
                        d="M11.584 2.376a.75.75 0 0 1 .832 0l9 6a.75.75 0 1 1-.832 1.248L12 3.901 3.416 9.624a.75.75 0 0 1-.832-1.248l9-6Z"
                        :fill="selectedBankAccount === bank.name ? 'white' : '#1E1B4B'"
                      />
                      <path
                        fill-rule="evenodd"
                        d="M20.25 10.332v9.918H21a.75.75 0 0 1 0 1.5H3a.75.75 0 0 1 0-1.5h.75v-9.918a.75.75 0 0 1 .634-.74A49.109 49.109 0 0 1 12 9c2.59 0 5.134.202 7.616.592a.75.75 0 0 1 .634.74Zm-7.5 2.418a.75.75 0 0 0-1.5 0v6.75a.75.75 0 0 0 1.5 0v-6.75Zm3-.75a.75.75 0 0 1 .75.75v6.75a.75.75 0 0 1-1.5 0v-6.75a.75.75 0 0 1 .75-.75ZM9 12.75a.75.75 0 0 0-1.5 0v6.75a.75.75 0 0 0 1.5 0v-6.75Z"
                        clip-rule="evenodd" :fill="selectedBankAccount === bank.name ? 'white' : '#1E1B4B'"
                      />
                      <path
                        d="M12 7.875a1.125 1.125 0 1 0 0-2.25 1.125 1.125 0 0 0 0 2.25Z" :fill="selectedBankAccount === bank.name ? 'white' : '#1E1B4B'"
                      />
                    </svg>
                    <span class="text-sm">{{ bank.name }}</span>
                  </div>
                </div>
              </div>
              <div>
                <h2 class="text-gray-600 mb-2">ALL BANKS</h2>
                <div class="h-[200px] overflow-y-auto mb-3">
                  <ul class="bg-gray-100 p-4 rounded space-y-2">
                    <li
                      v-for="bank in filteredAllBanks"
                      :key="bank.name"
                      class="flex items-center space-x-2 py-1 px-1 rounded-md hover:bg-[#1E1B4B] hover:text-white"
                      @click="setBankAccount(bank.name)"
                      :class="{
                        'bg-[#1E1B4B] text-white':
                          selectedBankAccount === bank.name,
                        'bg-gray-100': selectedBankAccount !== bank.name,
                      }"
                    >
                      <svg
                        xmlns="http://www.w3.org/2000/svg"
                        viewBox="0 0 24 24"
                        :fill="
                          selectedBankAccount === bank.name
                            ? 'white'
                            : '#1E1B4B'
                        "
                        class="h-4 w-4 "
                      >
                        <path
                          d="M11.584 2.376a.75.75 0 0 1 .832 0l9 6a.75.75 0 1 1-.832 1.248L12 3.901 3.416 9.624a.75.75 0 0 1-.832-1.248l9-6Z"
                        />
                        <path
                          fill-rule="evenodd"
                          d="M20.25 10.332v9.918H21a.75.75 0 0 1 0 1.5H3a.75.75 0 0 1 0-1.5h.75v-9.918a.75.75 0 0 1 .634-.74A49.109 49.109 0 0 1 12 9c2.59 0 5.134.202 7.616.592a.75.75 0 0 1 .634.74Zm-7.5 2.418a.75.75 0 0 0-1.5 0v6.75a.75.75 0 0 0 1.5 0v-6.75Zm3-.75a.75.75 0 0 1 .75.75v6.75a.75.75 0 0 1-1.5 0v-6.75a.75.75 0 0 1 .75-.75ZM9 12.75a.75.75 0 0 0-1.5 0v6.75a.75.75 0 0 0 1.5 0v-6.75Z"
                          clip-rule="evenodd"
                        />
                        <path
                          d="M12 7.875a1.125 1.125 0 1 0 0-2.25 1.125 1.125 0 0 0 0 2.25Z"
                        />
                      </svg>
                      <span>{{ bank.name }}</span>
                    </li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div v-if="setBankDetails">
          <div class="py-32 px-10">
              <AnimatedList
               :is-open="animatedVal"
              @close="animaSuccess"/>
          </div>
    
          
        </div>
        <div v-if="bankDetailsSuccess"><div class="min-h-screen  flex items-center justify-center ">
    <div class=" space-y-3">
      <div class="text-center">
        <div class="w-24 h-24 bg-green-100 rounded-full mx-auto flex items-center justify-center">
          <div class="w-12 h-12 text-green-500">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 21V5a2 2 0 00-2-2H7a2 2 0 00-2 2v16m14 0h2m-2 0h-5m-9 0H3m2 0h5M9 7h1m-1 4h1m4-4h1m-1 4h1m-5 10v-5a1 1 0 011-1h2a1 1 0 011 1v5m-4 0h4" />
            </svg>
          </div>
        </div>
        <h2 class="text-2xl font-bold mt-4">Bank account added</h2>
        <p class="text-gray-600 mt-2">Your bank details have been verified.</p>
      </div>

      <div class="bg-gray-50 rounded-lg p-10 space-y-2 ">
        <div class="flex items-center space-x-5">
          <div class="w-8 h-8 bg-blue-100 rounded-full flex items-center justify-center text-blue-500">
            <span class="text-lg font-semibold">A</span>
          </div>
          <div>
            <h3 class="font-semibold">Archana</h3>
            <p class="text-sm text-gray-500">{{selectedBankAccount}}</p>
          </div>
        </div>

        <div class="space-y-3">
          <div class="flex justify-between">
            <span class="text-gray-600 pr-10">Acc. No.</span>
            <span class="font-medium">XXXX XXXX 6636</span>
          </div>
          <div class="flex justify-between">
            <span class="text-gray-600 pr-10">IFSC Code</span>
            <span class="font-medium">1234567</span>
          </div>
          <div class="flex justify-between">
            <span class="text-gray-600 pr-10">Branch</span>
            <span class="font-medium"> THANJAVUR</span>
          </div>
        </div>
      </div>

      <button class="w-full animate-bounce bg-[#1E1B4B] text-white py-3 mt-10 mb-6 rounded-lg font-semibold hover:bg-[#1E1B4B] transition-colors"
      @click="completeBankDetails">
        Continue
      </button>
    </div>
  </div></div>
       
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";
import { useRouter } from "vue-router";
import { computed } from "vue";
import AnimatedList from '@/components/AnimatedList.vue';

const searchQuery = ref("");

const router = useRouter();
const isOpen = ref(false);
const verificationStep = ref(true);
const bankVerification = ref(false);
const selectedBankAccount = ref("");
const setBankDetails=ref(false)
const bankDetailsSuccess=ref(false)
const openBottomSheet = () => {
  isOpen.value = true;
};
const animationVal = ref(true);

const closeBottomSheet = () => {
  isOpen.value = false;
};
const nextStep = () => {
  verificationStep.value = false;
  bankVerification.value = true;
};

const popularBanks = ref([
  {
    name: "Axis Bank",
    logo: "https://storage.googleapis.com/a1aa/image/lTdfHGeZumnI2Eop0GOl4zfryBKePlhflNKKObNOksaBMWvdC.jpg",
  },
  {
    name: "HDFC Bank",
    logo: "https://storage.googleapis.com/a1aa/image/pRqD7yHPwloZIRdyG0ZZdPwU2u12SGszidDseJ4087nvY92JA.jpg",
  },
  {
    name: "ICICI Bank",
    logo: "https://storage.googleapis.com/a1aa/image/yHWEf7mzbSW0TaapfnEUs9 qbsWpKZ913fcWKzUAqYUVyi1bnA.jpg",
  },
  {
    name: "State Bank",
    logo: "https://storage.googleapis.com/a1aa/image/OnEs2VHVemynBaLsNJpY6ItJGagauRgxYfTDvd24nze8i1bnA.jpg",
  },
]);

const allBanks = ref([
  { name: "Axis Bank" },
  { name: "Bandhan Bank" },
  { name: "Bank of Baroda" },
  { name: "Bank of India" },
  { name: "HDFC Bank" },
  { name: "ICICI Bank" },
  { name: "State Bank of India" },
  { name: "Punjab National Bank" },
  { name: "Kotak Mahindra Bank" },
  { name: "IndusInd Bank" },
  { name: "Yes Bank" },
  { name: "Bank of Maharashtra" },
  { name: "Central Bank of India" },
  { name: "Union Bank of India" },
  { name: "Indian Bank" },
  { name: "UCO Bank" },
  { name: "Indian Overseas Bank" },
  { name: "Bank of America" },
  { name: "Citi Bank" },
  { name: "Deutsche Bank" },
]);

const filteredPopularBanks = computed(() => {
  return popularBanks.value.filter((bank) =>
    bank.name.toLowerCase().includes(searchQuery.value.toLowerCase())
  );
});

const filteredAllBanks = computed(() => {
  return allBanks.value.filter((bank) =>
    bank.name.toLowerCase().includes(searchQuery.value.toLowerCase())
  );
});

// Open the bottom sheet after 0.5 seconds
onMounted(() => {
  setTimeout(openBottomSheet, 100);
});
const setBankAccount = (bankName: string) => {
  selectedBankAccount.value = bankName;
  
  
  // After 2 seconds, set setBankDetails to true
  setTimeout(() => {
    bankVerification.value = false;
    setBankDetails.value = true;
  }, 1000); // 2000 ms = 2 seconds
};
const animaSuccess=() =>{
  setBankDetails.value = false;
  bankDetailsSuccess.value=true
}
const completeBankDetails =()=>{
    router.push('/FifthStep');
}
</script>
