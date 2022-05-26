<template>
  <div class="black-bg" v-if="nowModalOpenState">
    <div class="white-bg">
        <h4>{{ onerooms[modalClickId].title }}</h4>
        <p>{{ onerooms[modalClickId].content }}</p>
        <DiscountBanner></DiscountBanner>
        <button @click="nowModalOpenState=false;">닫기</button>
    </div>
  </div> 
</template>

<script>

 import DiscountBanner from "../components/DiscountBanner.vue";

export default {
  name: 'ModalDetail',
  props: {
    onerooms: Object,
    modalOpenState: Boolean,
    modalClickId: Number,
  },
  data() {
    return {
      nowModalOpenState : this.modalOpenState,
    }
  },
  methods : {
    
  },
   components: {
      DiscountBanner : DiscountBanner,
   }
}

</script>


<style scoped>

</style>
               