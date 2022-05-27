<template>
  
  <div>
    
    <transition name = "fade">
      <ModalDetail 
        :onerooms=onerooms :modalOpenState=modalOpenState :modalClickId=modalClickId 
        @fnModalClose = 'fnModalClose'
      />
    </transition>

    <div class="menu">
      <a v-for="(menu,i) in menus" :key="i">{{ menu }}-{{ i }}</a>
    </div>

    <DiscountBanner v-if="showDiscount == true" 
      :discountValue="discountValue"
      @fnDiscountValueMinus="fnDiscountValueMinus" 
    />

    <button @click="fnPriceSort">가격순 정렬</button>
    <button @click="fnPriceSortBack">정렬복구</button>
    

    <ProductCard 
      v-for="oneroom in onerooms" :key="oneroom.id" 
      :oneroom=oneroom :modalOpenState=modalOpenState :modalClickId=modalClickId 
      @fnModalView='fnModalView'
    />

    

  </div>
</template>

<script>

import data from "./assets/oneroom.js";

import ProductCard from "./components/ProductCard.vue";
import ModalDetail from "./components/ModalDetail.vue";
import DiscountBanner from "./components/DiscountBanner.vue";

export default {
  name: 'App',
  data() {
    return {
      menus : ['Home', 'Shop', 'About'],
      onerooms : data,
      onerooms_origin : [...data],
      modalOpenState : false,
      modalClickId : 0,
      showDiscount : true,
      discountValue : 30,
    }
  },
  methods : {

    fnModalView : function(id){
      console.log('------- fnModalView : '+id);
      this.modalClickId = id;
      this.modalOpenState = true;
    },
    fnModalClose : function(){
      console.log('------- fnModalClose : ');
      this.modalClickId = null;
      this.modalOpenState = false;
    },
    fnPriceSort : function(){
      this.onerooms.sort(function(a,b){
        return a.price - b.price
        //return b.price - a.price
      });
    },
    fnPriceSortBack : function(){
      this.onerooms = [...this.onerooms_origin];
    },
    fnDiscountValueMinus : function(){

      var discountInterval = setInterval(() => {
        this.discountValue = this.discountValue - 1
        if( this.discountValue == 0 ){
          clearInterval(discountInterval);
        }
      }, 1000);

    },

  },

  /*mounted(){

    setTimeout(()=>{
      this.showDiscount = false;
    }, 2000);

  },*/

  components: {
    ModalDetail : ModalDetail,
    ProductCard : ProductCard,
    DiscountBanner : DiscountBanner,
  }
}


</script>

<style>

.fade-enter-from{ opacity: 0;}
.fade-enter-active{ transition: all 1s; }
.fade-enter-to{ opacity: 1;}

.fade-leave-from{ opacity: 1;}
.fade-leave-active{ transition: all 1s; }
.fade-leave-to{ opacity: 0;}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background : darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color : white;
  padding: 10px;
}

.room-img {
  width: 270px;
  margin-top: 40px;
}

body{
  margin:0px;
}
div{
  box-sizing: border-box;
}
.black-bg{
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg{
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

.discountMain{
  width: 100%;
  background-color: beige;
  padding :10px;
}

</style>
