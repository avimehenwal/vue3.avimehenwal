<template>
  <div class="about">
    <h1>This is an about page</h1>
    <p>Role based menu example</p>
    <ul v-for="menu in menuItems" :key="menu.name">
      <li v-if="menu.isMenuAllowed()">{{ menu.icon }} -> {{ menu.name }}</li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

const isAuthenticated = true;
const isAdmin = true;

const menuItems = ref([
  {
    name: "first_menu",
    icon: "icon1",
    isMenuAllowed: () => (isAuthenticated ? true : false),
  },
  {
    name: "second_menu",
    icon: "icon2",
    isMenuAllowed: () => (isAuthenticated && isAdmin ? true : false),
  },
]);
</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
