<template>
  <div class="black-bg" v-if="nowModalOpenState">
    <div class="white-bg">
        <h4>{{ onerooms[modalClickId].title }}</h4>
        <p>{{ onerooms[modalClickId].content }}</p>
        <Discount></Discount>
        <button @click="nowModalOpenState=false;">닫기</button>
    </div>
  </div>
</template>

<script>

// import Discount from "./components/DiscountBanner.vue";

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
    // Discount : Discount,
  }
}

</script>


<style scoped>

</style>
               