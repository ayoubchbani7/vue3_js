<template>
  <div>Hello world {{ firstName }} {{ lastName }} {{ count }}</div>
  <button @click="increment">Increment</button>
  <button @click="decrement">Decrement</button>
  <div v-show="count > 5">Count is greater than 0</div>
</template>

<script setup>
import { ref } from "vue";
const firstName = "John";
const lastName = "Doe";
const count = ref(0);
console.log(count, count.value);
const increment = (event) => {
  count.value++;
  console.log(event);
};
const decrement = () => {
  count.value--;
};
</script>

<style scoped>
div {
  color: red;
  font-weight: bold;
  font-size: 20px;
  text-align: center;
  margin-top: 20px;
  margin-bottom: 20px;
  margin-left: 20px;
  margin-right: 20px;
  padding: 20px;
  border: 1px solid red;
  border-radius: 10px;
  box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.5);
  transition: all 0.3s ease;
  &:hover {
    background-color: blue;
    color: white;
  }
}
</style>
