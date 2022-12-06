<script>
import { computed } from "@vue/reactivity";
import ITEMS from "./items.json";
  export default {
    data() {
      return {
        numberA: 5,
        numberB: 16,
        items: ITEMS,
        message: "This is a normal message",
      }
    },
    computed: {
      itemName(){
        return this.items[0].name;
      },
      cartLimit(){
        return this.items.length >= 5;
      },
    }
  }
</script>

<template>
  <p class="text-right m-6">{{(numberA + numberB)}} April, 2022</p>
  <p class="text-3xl m-6">The {{itemName}} Project</p>
  <div class="border-2 border-blue-500">
    <div v-for="item of items" key="item.uuid" class="flex justify-evenly my-8">
      <h3 class="text-xl font-bold">{{item.name}}</h3>
      <div class="flex flex-col items-center">
        <img :src="item.image" :alt="item.name" class="w-16">
        <p>{{item.description}}</p>
      </div>
      <p>{{item.price}}</p>
    </div>
  </div>
  <div>
    <button v-if="cartLimit" class="float-right m-12 border-2 border-blue-500 p-2">Confirm purchase</button>
    <p v-else>You need to add more products</p>
  </div>
</template>

<style scoped>

</style>
