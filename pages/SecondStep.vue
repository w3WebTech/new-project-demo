<template>
  <div class="min-h-screen bg-[#ECE8FF] relative overflow-hidden font-inter">
    <div
      class="fixed inset-0 bg-[#FF844B]  z-40"
      v-if="isOpen"
      @click="closeBottomSheet"
    >
      <div class="flex justify-between">
        <div></div>
        <div class="p-7 text-xl text-white font-bold font-serif">goodwill</div>
      </div>
    </div>
    <div
      class="fixed h-[90%] bottom-0 left-0 right-0 bg-white z-50 transition-transform transform rounded-t-xl"
      :class="{ 'translate-y-0': isOpen, 'translate-y-full': !isOpen }"
    >
      <div class="md:w-[40%] md:flex md:mx-auto md:justify-center md:items-center">
        <!-- <div class="absolute inset-0 grid grid-cols-12 h-[300px]">
        <div v-for="i in 48" :key="i" class="border border-[#dad3fc]"></div>
      </div> -->
        <div v-if="isStepPage">
          <div class="md:pt-5 sm:pt-10 pb-5 relative">
            <!-- <div class="flex items-center justify-center text-center">
          <img
            src="public/images/ventura.jpeg"
            alt="Google"
            class="w-30 h-30"
          />
        </div> -->
            <div
              class="text-3xl font-bold py-1 flex items-center md:justify-start sm:justify-center px-3 text-center"
            >
              Here's what's next
            </div>
            <div class="rounded-lg px-2">
              <div class="flex flex-col">
                <div class="flex items-center align-center space-x-10">
                  <div class="bg-purple-200 rounded-full p-3">
                    <svg
                      class="w-4 h-4 text-gray-500"
                      fill="none"
                      viewBox="0 0 24 24"
                      stroke="currentColor"
                    >
                      <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="2"
                        d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z"
                      />
                    </svg>
                  </div>
                  <div class="mb-5">
                     

                    <h3 class="text-md font-bold">Complete e-KYC</h3>
                    <p class="text-gray-600 text-sm">
                      Keep your Aadhaar and PAN card handy
                    </p>
                  </div>
                </div>
                <div class="flex items-center space-x-10">
                  <div class="bg-purple-200 rounded-full p-3">
                    <svg
                      class="w-4 h-4 text-gray-500"
                      fill="none"
                      viewBox="0 0 24 24"
                      stroke="currentColor"
                    >
                      <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="2"
                        d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z"
                      />
                    </svg>
                  </div>
                  <div class="mb-5">
                     

                    <div class="text-md font-bold">Setup Your Profile</div>
                    <div class="text-gray-600 text-sm">
                      Answer a few question about yourself
                    </div>
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
                        d="M15.75 6a3.75 3.75 0 1 1-7.5 0 3.75 3.75 0 0 1 7.5 0ZM4.501 20.118a7.5 7.5 0 0 1 14.998 0A17.933 17.933 0 0 1 12 21.75c-2.676 0-5.216-.584-7.499-1.632Z"
                      />
                    </svg>
                  </div>
                  <div class="mb-5">
                     

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
                  <div class="mb-5">
                     

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
                type="submit"
                class="w-full text-white rounded-lg py-2 mt-6 font-medium transition-colors disabled:cursor-not-allowed bg-[#1E1B4B] animate-bounce"
                    @click="nextStep"
              >
                Continue
              </button>
              </div>
            </div>
          </div>
        </div>
        <div v-if="isPanForm">
          <div class="max-w-md mx-auto p-6">
            <h1 class="text-2xl font-semibold text-[#2D3648] mb-1">
              Enter your PAN
            </h1>
            <p class="text-gray-500 text-sm mb-6">
              These details are required by SEBI to open your demat account.
            </p>

            <form @submit.prevent="handleSubmit" class="space-y-4">
              <!-- PAN Input -->
              <div>
                <label
                  for="pan"
                  class="block text-sm font-medium text-gray-600 mb-1"
                  >PAN</label
                >
                <input
                  v-model="form.pan"
                  type="text"
                  id="pan"
                  class="w-full px-4 py-3 rounded-lg border border-gray-300 focus:ring-2 focus:ring-[#1E1B4B] focus:bg-blue-50 transition-colors uppercase"
                  placeholder="AGMK566672"
                  maxlength="10"
                />
              </div>

              <!-- Name Input -->
              <div>
                <label
                  for="name"
                  class="block text-sm font-medium text-gray-600 mb-1"
                  >Name as per PAN</label
                >
                <input
                  v-model="form.name"
                  type="text"
                  id="name"
                  class="w-full px-4 py-3 rounded-lg border border-gray-300 focus:ring-2 focus:ring-[#1E1B4B] focus:bg-blue-50 transition-colors"
                  placeholder="NAME"
                />
              </div>

              <!-- DOB Input -->
              <div>
                <label
                  for="dob"
                  class="block text-sm font-medium text-gray-600 mb-1"
                  >DOB</label
                >
                <div class="relative">
                  <input
                    v-model="form.dob"
                    type="text"
                    id="dob"
                    class="w-full px-4 py-3 rounded-lg border border-gray-300 focus:ring-2 focus:ring-[#1E1B4B] focus:bg-blue-50 transition-colors"
                    placeholder="DD/MM/YYYY"
                    readonly
                  />
                  <button
                    type="button"
                    class="absolute right-3 top-1/2 transform -translate-y-1/2"
                    @click="showDatePicker = true"
                  >
                    <svg
                      class="w-5 h-5 text-gray-400"
                      fill="none"
                      stroke="currentColor"
                      viewBox="0 0 24 24"
                    >
                      <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="2"
                        d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"
                      />
                    </svg>
                  </button>
                </div>
              </div>

              <!-- Tax Residency Checkbox -->
              <div class="flex items-start gap-3 mt-4">
                <div class="flex-shrink-0 mt-1">
                  <div
                    class="w-5 h-5 border-2 rounded-xl flex items-center justify-center cursor-pointer"
                    :class="
                      form.isTaxResident
                        ? 'border-emerald-500 bg-emerald-500'
                        : 'border-gray-300'
                    "
                    @click="form.isTaxResident = !form.isTaxResident"
                  >
                    <svg
                      v-if="form.isTaxResident"
                      class="w-3 h-3 text-white"
                      fill="none"
                      stroke="currentColor"
                      viewBox="0 0 24 24"
                    >
                      <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="3"
                        d="M5 13l4 4L19 7"
                      />
                    </svg>
                  </div>
                </div>
                <label
                  class="text-sm text-gray-600 leading-tight cursor-pointer"
                  @click="form.isTaxResident = !form.isTaxResident"
                >
                  I'm a tax resident of India and not paying taxes to any other
                  jurisdiction(s).
                </label>
              </div>

              <!-- Info Text -->
              <div
                class="mt-6 text-xs text-gray-500 bg-gray-50 p-1 rounded-t-xl leading-relaxed"
              >
                <span class="text-red-500">*</span> Your account would be opened
                as per your PAN card details. Please use the
                <span class="text-indigo-600"
                  >Offline Account Opening Form</span
                >
                if you are looking to open an HUF, Corporate, Partnership, Joint
                or NRI account.
              </div>

              <!-- Submit Button -->
              <button
                type="submit"
                class="w-full text-white rounded-lg py-2 mt-6 font-medium transition-colors disabled:cursor-not-allowed"
                :disabled="!isFormValid"
                :class="!isFormValid ? 'bg-gray-300' : 'bg-[#1E1B4B] animate-bounce'"
                @click="setPanDetails"
              >
                Continue
              </button>
            </form>
          </div>
        </div>
        <div v-if="isPanDetails">
          <div class="max-w-md mx-auto p-6 py-20">
            <h1 class="text-2xl font-semibold text-[#2D3648] mb-1">
              Enter your PAN
            </h1>
            <p class="text-gray-500 text-sm mb-6">
              These details are required by SEBI to open your demat account.
            </p>
            <div class="text-xl py-3 font-bold text-[#2D3648] ">{{ form.pan }}</div>
            <div class="bg-gray-100 border border-gray-200 rounded-md p-3">
              <div class="text-sm text-gray-500 py-2">Name</div>
              <div class="text-md font-bold text-[#2D3648]">{{ form.name }}</div>

              <div class="text-sm text-gray-500 py-2">
                Permanent Address Number
              </div>
              <div class="text-md font-bold text-[#2D3648]">{{ form.pan }}</div>
            </div>
            <div
              class="flex justify-center text-orange-500 font-bold text-sm py-5 cursor-pointer"
              @click="moveBack"
            >
              Not your Pan ? Try Again
            </div>

            <button
              type="submit"
              class="w-full text-white rounded-lg py-2 mt-6 font-medium transition-colors disabled:cursor-not-allowed"
              :disabled="!isFormValid"
              :class="!isFormValid ? 'bg-gray-300' : 'bg-[#1E1B4B] animate-bounce'"
              @click="moveToEkyc"
            >
              Continue
            </button>
          </div>
        </div>
        <div v-if="eKycFinalStep">
          <div class=" p-6  max-w-md">
            <div class="flex">
              <div class="mt-1 " @click="movePrev"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="gray" class="h-5 w-5">
  <path fill-rule="evenodd" d="M7.72 12.53a.75.75 0 0 1 0-1.06l7.5-7.5a.75.75 0 1 1 1.06 1.06L9.31 12l6.97 6.97a.75.75 0 1 1-1.06 1.06l-7.5-7.5Z" clip-rule="evenodd" />
</svg>
</div>
 <h1 class="text-xl font-semibold text-gray-800 mb-2 px-2">
              Complete e-KYC
            </h1></div>
           
            <p class="text-gray-600 mb-4">
              Make sure your mobile number is linked to your Aadhaar card.
            </p>
            <a href="https://uidai.gov.in/en/my-aadhaar/avail-aadhaar-services.html" class="text-orange-500 mb-6 block underline font-semibold" target="_blank" rel="noopener noreferrer">
            How to link Aadhaar with mobile?</a
            >
            <div class="bg-gray-100 p-4 rounded-lg mb-6">
              <h2 class="text-lg font-semibold text-gray-800 mb-4">
                How this works?
              </h2>
              <ul class="space-y-4">
                <li class="flex items-start">
                     <div class="bg-white rounded-lg border p-2">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="blue" class="h-4 w-4">
  <path fill-rule="evenodd" d="M5.625 1.5H9a3.75 3.75 0 0 1 3.75 3.75v1.875c0 1.036.84 1.875 1.875 1.875H16.5a3.75 3.75 0 0 1 3.75 3.75v7.875c0 1.035-.84 1.875-1.875 1.875H5.625a1.875 1.875 0 0 1-1.875-1.875V3.375c0-1.036.84-1.875 1.875-1.875Zm6.905 9.97a.75.75 0 0 0-1.06 0l-3 3a.75.75 0 1 0 1.06 1.06l1.72-1.72V18a.75.75 0 0 0 1.5 0v-4.19l1.72 1.72a.75.75 0 1 0 1.06-1.06l-3-3Z" clip-rule="evenodd" />
  <path d="M14.25 5.25a5.23 5.23 0 0 0-1.279-3.434 9.768 9.768 0 0 1 6.963 6.963A5.23 5.23 0 0 0 16.5 7.5h-1.875a.375.375 0 0 1-.375-.375V5.25Z" />
</svg>
</div>
                  <span class="text-gray-700 text-sm px-2"
                    >You will be redirected to Digilocker for e-KYC.</span
                  >
                </li>
                <li class="flex items-start">
                  <div class="bg-white rounded-lg border p-2">
                       <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="green" class="h-4 w-4">
  <path fill-rule="evenodd" d="M8.25 6.75a3.75 3.75 0 1 1 7.5 0 3.75 3.75 0 0 1-7.5 0ZM15.75 9.75a3 3 0 1 1 6 0 3 3 0 0 1-6 0ZM2.25 9.75a3 3 0 1 1 6 0 3 3 0 0 1-6 0ZM6.31 15.117A6.745 6.745 0 0 1 12 12a6.745 6.745 0 0 1 6.709 7.498.75.75 0 0 1-.372.568A12.696 12.696 0 0 1 12 21.75c-2.305 0-4.47-.612-6.337-1.684a.75.75 0 0 1-.372-.568 6.787 6.787 0 0 1 1.019-4.38Z" clip-rule="evenodd" />
  <path d="M5.082 14.254a8.287 8.287 0 0 0-1.308 5.135 9.687 9.687 0 0 1-1.764-.44l-.115-.04a.563.563 0 0 1-.373-.487l-.01-.121a3.75 3.75 0 0 1 3.57-4.047ZM20.226 19.389a8.287 8.287 0 0 0-1.308-5.135 3.75 3.75 0 0 1 3.57 4.047l-.01.121a.563.563 0 0 1-.373.486l-.115.04c-.567.2-1.156.349-1.764.441Z" />
</svg>
                  </div>
  
                  <span class="text-gray-700 text-sm px-2"
                    >It is a Govt. of India initiative with more than 150
                    million trusted users.</span
                  >
                </li>
                <li class="flex items-start">
                   <div class="bg-white rounded-lg border p-2">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="red" class="h-4 w-4">
  <path fill-rule="evenodd" d="M12 3.75a6.715 6.715 0 0 0-3.722 1.118.75.75 0 1 1-.828-1.25 8.25 8.25 0 0 1 12.8 6.883c0 3.014-.574 5.897-1.62 8.543a.75.75 0 0 1-1.395-.551A21.69 21.69 0 0 0 18.75 10.5 6.75 6.75 0 0 0 12 3.75ZM6.157 5.739a.75.75 0 0 1 .21 1.04A6.715 6.715 0 0 0 5.25 10.5c0 1.613-.463 3.12-1.265 4.393a.75.75 0 0 1-1.27-.8A6.715 6.715 0 0 0 3.75 10.5c0-1.68.503-3.246 1.367-4.55a.75.75 0 0 1 1.04-.211ZM12 7.5a3 3 0 0 0-3 3c0 3.1-1.176 5.927-3.105 8.056a.75.75 0 1 1-1.112-1.008A10.459 10.459 0 0 0 7.5 10.5a4.5 4.5 0 1 1 9 0c0 .547-.022 1.09-.067 1.626a.75.75 0 0 1-1.495-.123c.041-.495.062-.996.062-1.503a3 3 0 0 0-3-3Zm0 2.25a.75.75 0 0 1 .75.75c0 3.908-1.424 7.485-3.781 10.238a.75.75 0 0 1-1.14-.975A14.19 14.19 0 0 0 11.25 10.5a.75.75 0 0 1 .75-.75Zm3.239 5.183a.75.75 0 0 1 .515.927 19.417 19.417 0 0 1-2.585 5.544.75.75 0 0 1-1.243-.84 17.915 17.915 0 0 0 2.386-5.116.75.75 0 0 1 .927-.515Z" clip-rule="evenodd" />
</svg>
                   </div>

                  <span class="text-gray-700 text-sm px-2"
                    >You won't need to enter your details manually as the
                    required documents will be fetched from Digilocker.</span
                  >
                </li>
              </ul>
            </div>
            <button
              class="bg-[#1E1B4B] text-white py-2 px-4 rounded-lg w-full my-4 font-semibold animate-bounce"
              @click="moveToConfirmation"
            >
              Start e-KYC
            </button>
            <a  href="https://uidai.gov.in/en/my-aadhaar/avail-aadhaar-services.html" target="_blank" rel="noopener noreferrer"class="text-orange-500 block text-center font-semibold"
              >Mobile not linked with Aadhaar?</a
            >
          </div>
        </div>
        <div v-if="finalConfirmation">
            <div id="app" class="w-full max-w-md p-6 ">
              <div class="flex">
                <div class="mt-1.5" @click="MoveEkyc"> <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="gray" class="h-5 w-5">
  <path fill-rule="evenodd" d="M7.72 12.53a.75.75 0 0 1 0-1.06l7.5-7.5a.75.75 0 1 1 1.06 1.06L9.31 12l6.97 6.97a.75.75 0 1 1-1.06 1.06l-7.5-7.5Z" clip-rule="evenodd" />
</svg></div>
<h1 class="text-xl font-semibold text-[#2D3648] mb-1 px-2">Confirm your details</h1>
              </div>
      
      <p class="text-gray-600 mb-6">We have fetched your Aadhaar details from Digilocker.</p>
      <div class="bg-gray-100 p-4 rounded-lg mb-4">
     <div class="mb-4">
          <span class="text-gray-600">Name:</span>
          <span class="font-semibold text-gray-800 ml-2">{{form.name}}</span>
        </div>
        <div class="mb-2 flex items-center justify-between">
          <div><span class="text-gray-600">Father's Name:</span>
          <span class="font-semibold text-gray-800  px-2 py-1 rounded ml-2">Name</span></div>
          
          <div class="ml-2 text-orange-500">
          <a href="#" class="text-orange-500 text-sm font-semibold ml-auto">Edit ></a>
          </div>
        </div>
     <div class="mb-4">
          <span class="text-gray-600">DOB:</span>
          <span class="font-semibold text-gray-800  px-2 py-1 rounded">{{form.dob}}</span>
        </div>
     <div class="mb-4">
          <span class="text-gray-600">Gender:</span>
          <span class="font-semibold text-gray-800 px-2">male</span>
        </div>
     <div class="mb-4">
          <span class="text-gray-600">Address:</span>
          <span class="font-semibold text-gray-800  px-2 py-1 rounded">Nadu, India, 613204</span>
        </div>
     <div class="mb-4">
          <span class="text-gray-600">Aadhaar No:</span>
          <span class="font-semibold text-gray-800 px-2">xxxxxxxx8649</span>
        </div>
      </div>
      <div class="flex items-center py-5">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="orange" class="w-5 h-5 mx-2">
  <path d="M4.5 3.75a3 3 0 0 0-3 3v.75h21v-.75a3 3 0 0 0-3-3h-15Z" />
  <path fill-rule="evenodd" d="M22.5 9.75h-21v7.5a3 3 0 0 0 3 3h15a3 3 0 0 0 3-3v-7.5Zm-18 3.75a.75.75 0 0 1 .75-.75h6a.75.75 0 0 1 0 1.5h-6a.75.75 0 0 1-.75-.75Zm.75 2.25a.75.75 0 0 0 0 1.5h3a.75.75 0 0 0 0-1.5h-3Z" clip-rule="evenodd" />
</svg>

        <span class="text-gray-800 font-semibold text-sm">PAN linked with your Aadhaar Card</span>
        <a href="#" class="text-orange-500 font-semibold text-sm ml-auto pr-4">View ></a>
      </div>
      <button class="w-full bg-[#1E1B4B] animate-bounce text-white font-bold py-2 rounded-lg my-4" @click="completeEkyc">Continue</button>
    </div>
        </div>
      </div>
    </div>
  </div>
  <DatePicker
    v-model="form.dob"
    :is-open="showDatePicker"
    @close="showDatePicker = false"
  />
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";
import { useRouter } from 'vue-router';

const router = useRouter();
const isOpen = ref(false);
const isPanDetails = ref(false);
const openBottomSheet = () => {
  isOpen.value = true;
};

const closeBottomSheet = () => {
  isOpen.value = false;
};

// Open the bottom sheet after 0.5 seconds
onMounted(() => {
  setTimeout(openBottomSheet, 100);
});
const isPanForm = ref(false);
interface FormData {
  pan: string;
  name: string;
  dob: string;
  isTaxResident: boolean;
}

const form = ref<FormData>({
  pan: "",
  name: "",
  dob: "",
  isTaxResident: false,
});

const showDatePicker = ref(false);
const isStepPage = ref(true);
const isFormValid = computed(() => {
  return (
    form.value.pan.length === 10 &&
    form.value.name.length > 0 &&
    form.value.dob.length > 0 &&
    form.value.isTaxResident
  );
});
const eKycFinalStep=ref(false)
const finalConfirmation=ref(false)
const handleSubmit = () => {
  if (isFormValid.value) {
    console.log("Form submitted:", form.value);
    // Handle form submission
  }
};
const nextStep = () => {
  isStepPage.value = false;
  isPanForm.value = true;
};
const setPanDetails = () => {
  isPanForm.value = false;
  isPanDetails.value = true;
};
const moveToEkyc =()=>{
  isPanDetails.value = false;
  eKycFinalStep.value=true
}
const moveToConfirmation =()=>{
 eKycFinalStep.value=false
 finalConfirmation.value=true

}
const completeEkyc =()=>{
    router.push('/ThirdStep');
}
const moveBack =() =>{
  isPanDetails.value=false
  isPanForm.value=true
}
 const movePrev =()=>{
  eKycFinalStep.value=false
  isPanDetails.value=true
 }
 const MoveEkyc=()=>{
   finalConfirmation.value=false
  eKycFinalStep.value=true
 
 }
</script>
