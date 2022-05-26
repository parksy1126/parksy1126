<template>
  <div>
      <img :src="oneroom.image" class="room-img"/>
      <h4 class="red" :style="스타일" @click="parentModalView(oneroom.id)">{{ oneroom.title }}</h4>
      <p>{{ oneroom.price }} 만원</p>
  </div>
</template>

<script>

export default {
  name: 'ProductCard',
  props: {
    oneroom : Object,
    modalClickId : Number,
    modalOpenState : Boolean,
  },

  data() {
    return {
      스타일 : 'color : red; cursor:pointer;',
    }
  },

  methods : {

    parentModalView( id ){
      console.log( '============ id : '+id );
      this.$emit('fnModalView', id);
    }

  },
}

</script>


<style>

</style>
               