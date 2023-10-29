<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <div>
    <h1>허위매물 뷰동산</h1>
    <h4 class="room1" :style="스타일">{{ products.at(0) }}</h4>
    <p>{{ prices.at(0) }}</p>
  </div>
  <div>
    <h1>허위매물 뷰동산</h1>
    <h4 class="room1" :style="스타일">{{ products.at(1) }}</h4>
    <p>{{ prices.at(1) }}</p>
  </div>
  <div>
    <h1>허위매물 뷰동산</h1>
    <h4 class="room1" :style="스타일">{{ products.at(2) }}</h4>
    <p>{{ prices.at(2) }}</p>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      prices : [100, 40, 80],
      스타일 : 'color:blue'
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
  margin-top: 60px;
}
</style>
