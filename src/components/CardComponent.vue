<template>
  <div class="card bg-[#fff] rounded-[16px] flex flex-col items-center gap-[20px] p-[30px]">
                    <h3 class="text-center text-[22px] font-bold">{{ props.data.title }}</h3>
                      <img src="../images/Line 368.svg" alt="">
                      <div v-if="props.data.texts.length==1" class="font-medium max-w-[195px] text-center pb-[25px]">
                        <p><img src="../images/Vector.svg" alt="" class="inline" v-if="props.data.texts.length>1"> {{ props.data.texts[0] }}</p>
                      </div>
                      <div v-else-if="props.data.texts.length==3" class="font-medium text-left pb-[44px]">
                      <p v-for="(text,i) in props.data.texts" :key="i"><img src="../images/Vector.svg" alt="" class="inline"> {{ text }}</p>
                    </div>
                    <div v-else class="font-medium text-left">
                      <p v-for="(text,i) in props.data.texts" :key="i"><img src="../images/Vector.svg" alt="" class="inline"> {{ text }}</p>
                    </div>
                  <img src="../images/Line 368.svg" alt="">
                  <div class="flex">
                      <span v-if="/^\d+$/.test(props.data.price)" class="text-[24px] font-bold text-[#191919]">$</span>
                      <p v-if="/^\d+$/.test(props.data.price)" class="text-center text-[#191919]">
                        <span class="text-[46px] font-bold">{{ props.data.price }}</span>
                        <span  class="text-[16px] font-bold">/month</span>
                      </p>
                      <p v-else class="text-center pt-[25px] text-[#191919]">
                        <span class="text-[30px] font-bold">{{ props.data.price }}</span>
                      </p>
                  </div>
                  <button v-if="props.data.price!=0" class="text-[#04A777] border-2 border-[#04A777] rounded-[32px] text-[14px] font-semibold p-[9px] pl-[23px] pr-[23px]">Buy Now</button>
                  <button v-else class="text-[#fff] border-2 border-[#FF6823] bg-[#FF6823] rounded-[32px] text-[14px] font-semibold p-[9px] pl-[23px] pr-[23px]">Start Now</button>
              </div>
</template>


<script setup>
import {defineProps} from 'vue'
const props=defineProps({
  data:Object
})
</script>


<style scoped>
h3{
transition: transform 0.5s

}
.card{
box-shadow: 0px 0px 17px 0px #00000017;
}
.card:hover h3{
transform: scale(1.6);
}
</style>