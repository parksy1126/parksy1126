<template>
  
  <div>
    
    <ModalDetail 
      :onerooms=onerooms :modalOpenState=modalOpenState :modalClickId=modalClickId 
      @fnModalClose = 'fnModalClose'
    />

    <div class="menu">
      <a v-for="(menu,i) in menus" :key="i">{{ menu }}-{{ i }}</a>
    </div>

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

export default {
  name: 'App',
  data() {
    return {
      menus : ['Home', 'Shop', 'About'],
      onerooms : data,
      modalOpenState : false,
      modalClickId : 0,

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

  },
  components: {
    ModalDetail : ModalDetail,
    ProductCard : ProductCard,
  }
}


</script>

<style>
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


</style>
