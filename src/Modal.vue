<template>
  <div class="black-bg" v-if="modalStatus">
    <div class="white-bg">
      <button class="closeModal" @click="$emit('closeModal')">X</button>
      <h4>상세페이지</h4>
      <img :src="products[target].image" style="height: 80%;">
      <p>{{products[target].title}}</p>
      <p>{{products[target].content}}</p>
<!--      <input @input="month=$event.target.value"/> v-model로 축소가능(vue문법) -->
      <input v-model.number="month"/>
      <p> {{month}}개월 선택하셨습니다 : {{products[target].price*month}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalComponent',
  data(){
    return{
      month : 1,
    }
  },
  watch: {
    month(a) {
      if (a && !/^\d+$/.test(a)) {
        alert('숫자만 입력하세요');
        this.month=1;
      }else if(a > 13){
        alert('13미만만 입력하세요');
        this.month=1;
      }
    }
  },
  props: {
    products: Array,
    target: Number,
    modalStatus: Boolean,
  },

}
</script>

<style>
input{
  width: 200px;
  align-self: center;
}
</style>
