
<template>
<div class="md:hidden">
 <!-- <OnBoardingSlider /> -->
 <LoginPage/>
</div>
<div class="sm:hidden overflow-hidden">
   <div class="grid grid-cols-2">
    <div><SliderForDesktop/></div>
    <div>
      <div class=" "><LoginPage/></div>
    </div>
   </div>
</div>
 
</template>

<script lang="ts">
import OnBoardingSlider from '@/components/OnBoardingSlider.vue'; // Use alias @ to point to the components directory
import SliderForDesktop from '@/components/SliderForDesktop.vue';
import LoginPage from '@/components/LoginPage.vue';
export default {
  components: {
    OnBoardingSlider,
    SliderForDesktop,
    LoginPage
  }
}
</script>