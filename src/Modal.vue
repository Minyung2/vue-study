<template>
  <div class="black-bg" v-if="changeModal==true">
    <div class="white-bg">
      <button class="closeModal" @click="changeModal=false">X</button>
      <h4>상세페이지</h4>
      <img :src="products[target].image" style="height: 80%;">
      <p>{{products[target].title}}</p>
      <p>{{products[target].content}}</p>
      <p>{{products[target].price}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalComponent',
}
</script>

<style>

</style>
