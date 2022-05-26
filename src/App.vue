<template>
  
  <div>
    <ModalDetail :onerooms=onerooms :modalOpenState=modalOpenState :modalClickId=modalClickId></ModalDetail>
    

    <div class="menu">
      <a v-for="(menu,i) in menus" :key="i">{{ menu }}-{{ i }}</a>
    </div>

    

    <div v-for="oneroom in onerooms" :key="oneroom.id">
      <img :src="oneroom.image" class="room-img"/>
      <h4 class="red" :style="스타일" @click="fnModalView(oneroom.id)">{{ oneroom.title }}</h4>
      <p>{{ oneroom.price }} 만원</p>
    </div>


    <!-- <div>
      <h4 class="red" :style="스타일">{{ products[0] }}</h4>
      <p>10 만원</p>
      <button @click="fnReport(0)">허위매물신고</button> <span>신고수 : {{ reportCnt[0] }}</span>
    </div>
    <div>
      <h4 class="red" :style="스타일">{{ products[1] }}</h4>
      <p>20 만원</p>
      <button @click="fnReport(1)">허위매물신고</button> <span>신고수 : {{ reportCnt[1] }}</span>
    </div>
    <div>
      <h4 class="red" :style="스타일">{{ products[2] }}</h4>
      <p>15 만원</p>
      <button @click="fnReport(2)">허위매물신고</button> <span>신고수 : {{ reportCnt[2] }}</span>
    </div> -->

  </div>
</template>

<script>

import data from "./oneroom.js";

import ModalDetail from "./components/ModalDetail.vue";

export default {
  name: 'App',
  data() {
    return {
      price1 : 60,
      스타일 : 'color : red; cursor:pointer;',
      menus: ['Home','Shop','About'],
      products: ['역삼원룸','천호원룸','마포원룸'],
      prices: ['10','20','10'],
      reportCnt: [0, 0, 0],
      onerooms : data,
      modalOpenState : false,
      modalClickId : 0,
    }
  },
  methods : {
    fnReport : function (id){
      console.log(id);
      this.reportCnt[id] = this.reportCnt[id] + 1;
    },
    fnModalView : function(id){
      console.log('-------'+id);
      this.modalClickId = id;
      this.modalOpenState = true;
    },
  },
  components: {
    ModalDetail : ModalDetail,
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
