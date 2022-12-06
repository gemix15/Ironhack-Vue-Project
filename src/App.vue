<script>
import { computed } from "@vue/reactivity";
import ITEMS from "./items.json";
  export default {
    data() {
      return {
        items: ITEMS,
        logo: "Ironhack_logo.svg",
        user: "user.png",
        shoppingCart: "cart.png",
      }
    },
    computed: {
      cartLimit(){
        return this.items.length >= 5;
      },
      numberOfItems(){
        return this.items.length;
      }
    }
  }
</script>

<template>
  <nav class="flex flex-row justify-between mx-8 my-4">
    <img :src="logo" alt="Ironhack logo">
    <ul class="flex ">
      <li class="mx-20 text-lg text-violet-900 hover:font-bold"><a href="#">Home</a></li>
      <li class="mx-20 text-lg text-violet-900 hover:font-bold"><a href="#">Services</a></li>
      <li class="mx-20 text-lg text-violet-900 hover:font-bold"><a href="#">Shop</a></li>
    </ul>
    <div class="flex">
      <img :src="user" alt="user profile" class="h-6 mx-8">
      <img :src="shoppingCart" alt="cart" class="h-6">
      <div class="mx-4 font-bold">{{numberOfItems}}</div>
    </div>
  </nav>
  <table class="w-3/4 my-20 bg-slate-200 mx-auto">
    <tr v-for="item of items" key="item.uuid" class="flex justify-between">
      <td><img :src="item.image" :alt="item.name" class="w-16"></td>
      <td class="text-lg font-bold mx-4">{{item.name}}</td>
      <td>{{item.price}}</td>
      <td><input type="number" v-model="item.quantity" placeholder="0" class="border-2 mx-16"></td>
      <td>{{(item.quantity * item.price)}}</td>
    </tr>
  </table>
  <div>
    <button v-if="cartLimit" class="float-right m-12 border-2 border-violet-500 p-2">Confirm purchase</button>
    <p v-else>Add at least 5 products for free shipping!</p>
  </div>
</template>

<style scoped>

</style>


