<template>
  <div class="menu">
    <a v-for="(menu, i) in menus" :key="i">{{ menu }}</a>
  </div>
  <img alt="Vue logo" src="./assets/logo.png">
  <h1>허위매물 뷰동산</h1>
  <div>
    <h4 class="rooms" :style="스타일">{{ products[0] }}</h4>
    <p>{{ prices[0] }} 만원</p>
    <button @click="increaseReport(0)">허위매물신고</button>
    <span>신고수 : {{ 신고수[0] }}</span>
  </div>
  <div>
    <h4 class="rooms" :style="스타일">{{ products[1] }}</h4>
    <p>{{ prices.at(1) }} 만원</p>
    <button @click="increaseReport(1)">허위매물신고</button>
    <span>신고수 : {{ 신고수[1] }}</span>
  </div>
  <div>
    <h4 class="rooms" :style="스타일">{{ products[2] }}</h4>
    <p>{{ prices.at(2) }} 만원</p>
    <button @click="increaseReport(2)">허위매물신고</button>
    <span>신고수 : {{ 신고수[2] }}</span>
  </div>
  <div v-for="(a,i) in products" :key="i">
    <h4 class="rooms" :style="스타일">{{ products[i] }}</h4>
    <p>{{ prices[i] }} 만원</p>
    <button @click="increaseReport(i)">허위매물신고</button>
    <span>신고수 : {{ 신고수[i] }}</span>
  </div>

</template>

<script>


export default {
  name: 'App',
  data() {
    return {
      신고수: [0,0,0],
      menus: ['Home', 'Shop', 'About'],
      products: ['역삼동원룸', '천호동원룸', '마포구원룸'],
      prices: [100, 40, 80],
      스타일: 'color:blue',
    }
  },
  methods: {
    increaseReport(index) {
      this.신고수[index]++;
    }
  },

  components: {}
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
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}
</style>
