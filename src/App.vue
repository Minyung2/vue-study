

<template>
  <div class="menu">
    <a v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
  </div>

  <DiscountComponent/>
  <ModalComponent/>


  <img alt="Vue logo" src="./assets/logo.png">
  <h1>허위매물 뷰동산</h1>
<!--  <div @click="changeModal=true">
    <img src="./assets/room0.jpg" class="room-img">
    <h4 class="rooms" :style="스타일">{{ products[0] }}</h4>
    <p>{{ prices[0] }} 만원</p>
    <button @click="increaseReport(0)">허위매물신고</button>
    <span>신고수 : {{ 신고수[0] }}</span>
  </div>
  <div>
    <img src="./assets/room1.jpg" class="room-img">
    <h4 class="rooms" :style="스타일">{{ products[1] }}</h4>
    <p>{{ prices.at(1) }} 만원</p>
    <button @click="increaseReport(1)">허위매물신고</button>
    <span>신고수 : {{ 신고수[1] }}</span>
  </div>
  <div>
    <img src="./assets/room2.jpg" class="room-img">
    <h4 class="rooms" :style="스타일">{{ products[2] }}</h4>
    <p>{{ prices.at(2) }} 만원</p>
    <button @click="increaseReport(2)">허위매물신고</button>
    <span>신고수 : {{ 신고수[2] }}</span>
  </div>-->
<!--  <div v-for="(a,i) in products" :key="i" @click="changeModal=true">
    <img :src="require(`@/assets/room${i}.jpg`)" class="room-img">
    <h4 class="rooms" :style="스타일">{{ products[i] }}</h4>
    <p>{{ prices[i] }} 만원</p>
    <button @click="increaseReport(i)">허위매물신고</button>
    <span>신고수 : {{ 신고수[i] }}</span>
  </div>-->
  <div v-for="(a,i) in products" :key="i" @click="changeModal=true; target=i">
    <img :src="a.image" class="room-img">
    <h4>{{a.title}}</h4>
    <p>{{a.price}}</p>
  </div>

</template>

<script>

import products from './assets/oneroom';
import DiscountComponent from "@/Discount.vue";
import ModalComponent from "@/Modal.vue";
export default {
  name: 'App',
  data() {
    return {
      target : 0,
      products : products,
      changeModal: false,
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

  components: {ModalComponent, DiscountComponent}
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
