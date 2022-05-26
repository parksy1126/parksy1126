<template>
  <div class="black-bg" v-if="modalOpenState">
    <div class="white-bg">
        <img :src="onerooms[modalClickId].image" />
        <h4>{{ onerooms[modalClickId].title }}</h4>
        <p>{{ onerooms[modalClickId].content }}</p>
        <p>{{ onerooms[modalClickId].price }}</p>
        <DiscountBanner></DiscountBanner>
        <button @click="parentModalClose">닫기</button>
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
  watch : {
    modalOpenState(){
      if( this.modalOpenState ){
        console.log('modalOpenState : '+this.modalOpenState);
        
      }
    }
  },
  data() {
    return {
      
    }
  },
  methods : {
    parentModalClose(){
      this.$emit('fnModalClose');
    }
  },
   components: {
      DiscountBanner : DiscountBanner,
   }
}

</script>


<style>

</style>
               