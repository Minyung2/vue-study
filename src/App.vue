

<template>
  <div class="menu">
    <a v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
  </div>

  <DiscountComponent/>
  <ModalComponent :products="products" :target="target" v-model:modalStatus="modalStatus"/>


  <img alt="Vue logo" src="./assets/logo.png">
  <h1>허위매물 Vue동산</h1>
  <ProductCard :product="products[i]" @openModal="modalStatus = true; target = $event"  v-for="(product,i) in products" :key="i"/>
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
      target : 0,
      products : products,
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
    }
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
body {
  margin: 0
}

div {
  box-sizing: border-box;
}

.discount{
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
  height: 95%;
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
