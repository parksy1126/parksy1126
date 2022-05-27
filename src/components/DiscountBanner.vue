<template>
  <div class="discount">
    {{discountValue}}% 할인 들어갑니다.
  </div>
</template>

<script>
export default {
  name: 'DiscountBanner',
  data() {
    return {
      
    }
  },
  props : {
    discountValue : Number,
  },
  mounted(){
    this.$emit('fnDiscountValueMinus');
  },
  methods : {
    
  },
  components: {
    
  }
}
</script>


<style scoped>
.discount{
  width: 100%;
  background-color: beige;
  padding :10px;
}
</style>
               