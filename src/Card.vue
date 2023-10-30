<template>
  <div v-for="(a,i) in products" :key="i" @click="openModal(); target=i">
    <img :src="a.image" class="room-img">
    <h4>{{a.title}}</h4>
    <p>{{a.price}}</p>
  </div>
</template>

<script>
export default {
  name: 'ProductCard',
  props :{
    products : Array,
    modalStatus : Boolean,
  },
  methods: {
    openModal() {
      this.$emit('update:modalStatus', true);
    }
  }
}
</script>

<style>

</style>
