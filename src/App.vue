<template>
  
  <div class="menu">
    <a v-for="(menu,i) in menus" :key="i">{{ menu }}-{{ i }}</a>
  </div>

  <!-- <div v-for="(product,i) in products" :key="i">
    <h4 class="red" :style="스타일">{{ product }}</h4>
    <p>{{ prices[i] }} 만원</p>
  </div> -->

  <div>
    <h4 class="red" :style="스타일">{{ products[0] }}</h4>
    <p>10 만원</p>
    <button @click="fn">허위매물신고</button> <span>신고수 : {{ reportCnt[0] }}</span>
  </div>
  <div>
    <h4 class="red" :style="스타일">{{ products[1] }}</h4>
    <p>20 만원</p>
    <button @click="fn">허위매물신고</button> <span>신고수 : {{ reportCnt[1] }}</span>
  </div>
  <div>
    <h4 class="red" :style="스타일">{{ products[2] }}</h4>
    <p>15 만원</p>
    <button @click="fn">허위매물신고</button> <span>신고수 : {{ reportCnt[2] }}</span>
  </div>

</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      price1 : 60,
      스타일 : 'color : red',
      menus: ['Home','Shop','About'],
      products: ['역삼원룸','천호원룸','마포원룸'],
      prices: ['10','20','10'],
      reportCnt: [0, 0, 0]
    }
  },
  components: {
    
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

</style>
