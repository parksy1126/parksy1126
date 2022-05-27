<template>
  <div class="black-bg" v-if="modalOpenState">
    <div class="white-bg">
        <img :src="onerooms[modalClickId].image" class="room-img"/>
        <h4>{{ onerooms[modalClickId].title }}</h4>
        <p>{{ onerooms[modalClickId].content }}</p>
        <p>{{ onerooms[modalClickId].price }}</p>
        <input v-model="month" />
        <p>
          {{ month }}개월
          , 총 {{ onerooms[modalClickId].price * month }} 원
        </p>
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
    },
    month(thisValue, befValue){
      
      var regTemp = /[^0-9.]/g;
      console.log( regTemp.exec(thisValue) );
      console.log( regTemp.exec(thisValue) !== null );
      
      if( regTemp.exec(thisValue) !== null ){
        alert('숫자만 입력가능');
        this.month = befValue;
      }else{
        if( thisValue > 12 ){
          alert('12보다 크게 안됨');
          this.month = befValue;
        }
      }
      
    }
  },
  beforeUpdate(){
    console.log( 'update start' );
    if( this.month == 2 ){
      alert('2개월은 안됩니다.');
    }
  },
  data() {
    return {
      month : 1,
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
.room-img {
  width: 270px;
  margin-top: 40px;
}
</style>
               