<template>
  <div class="menu">
    <a v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
  </div>

  <DiscountComponent :discountRate="discountRate" v-if="showDiscount==true"/>
  <button @click="priceSort">가격순 정렬</button>
  <button @click="resetSort">되돌리기</button>


  <transition name="fade">
    <ModalComponent @closeModal="modalStatus=false" :products="products" :target="target"
                    v-model:modalStatus="modalStatus"/>
  </transition>


  <img alt="Vue logo" src="./assets/logo.png">
  <h1>허위매물 Vue동산</h1>
  <ProductCard :product="products[i]" @openModal="modalStatus = true; target = $event" v-for="(product,i) in products"
               :key="i"/>
</template>

<script>

import products from './assets/oneroom';
import DiscountComponent from "@/Discount.vue";
import ModalComponent from "@/Modal.vue";
import ProductCard from "@/Card.vue";


export default {
  name: 'App',
  data() {
    return {
      discountRate: 30,
      showDiscount: true,
      target: 0,
      originalProducts: [...products],
      products: products,
      modalStatus: false,
      신고수: [0, 0, 0],
      menus: ['Home', 'Shop', 'About'],
      /*products: ['역삼동원룸', '천호동원룸', '마포구원룸'],*/
      prices: [100, 40, 80],
      스타일: 'color:blue',
    }
  },
  methods: {
    increaseReport(index) {
      this.신고수[index]++;
    },
    priceSort() {
      this.products.sort(function (a, b) {
        return a.price - b.price;
      });
    },
    resetSort() {
      return this.products = [...this.originalProducts];
    },
  },
  mounted() {
    setInterval(()=>{
      if(this.discountRate==0){
        this.showDiscount=false;
      }else {
        this.discountRate--;
      }
    },1000);
  },
  components: {ProductCard, ModalComponent, DiscountComponent}
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

.fade-enter-from {
  opacity: 0;
}

.fade-enter-active {
  transition: all 1s;
}

.fade-enter-to {
  opacity: 1;
}

.fade-leave-from {
  opacity: 1;
}

.fade-leave-active {
  transition: all 1s;
}

.fade-leave-to {
  opacity: 0;
}


body {
  margin: 0
}

div {
  box-sizing: border-box;
}

.discount {
  background: #eee;
  padding: 10px;
  margin-top: 10px;
  border-radius: 5px;
}

.closeModal {
  border-radius: 5px;
  background: transparent;
  border-color: transparent;
  font-size: 30px;
  margin-rigt: 100px;
  align-self: flex-end;
}


.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  height: 80%;
  background: white;
  border-radius: 8px;
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  overflow: auto;
}

.menu {
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 50%;
  margin-top: 50px;
}
</style>
