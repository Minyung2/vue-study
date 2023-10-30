<template>
  <div @click="openModal">
    <img :src="product.image" class="room-img">
    <h4>{{product.title}}</h4>
    <p>{{product.price}}</p>
  </div>
</template>

<script>
export default {
  name: 'ProductCard',
  props :{
    product : Object,
    modalStatus : Boolean,
  },
  methods: {
    openModal() {
      this.$emit('openModal', this.product.id);
    }
  }
}
</script>

<style>

</style>
