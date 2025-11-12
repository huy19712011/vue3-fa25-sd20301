<!-- eslint-disable no-unused-vars -->
<script setup>
import { ref } from "vue";
import { RouterLink, RouterView } from "vue-router";

const header = ref("Shopping List Application");

const items = ref([
  { id: 1, label: "10 product 1" },
  { id: 2, label: "20 product 2" },
  { id: 3, label: "3 product 3" },
  { id: 2, label: "4 product 4" },
]);

const newItem = ref("");

const newItemHighPriority = ref(false);

const saveItem = () => {
  items.value.push({ id: items.value.length + 1, label: newItem.value });
  newItem.value = "";
};
</script>

<template>
  <header>
    <nav class="navbar navbar-expand-lg bg-body-tertiary">
      <div class="container-fluid">
        <RouterLink class="navbar-brand" to="/">Navbar</RouterLink>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <RouterLink class="nav-link active" aria-current="page" to="/">Home</RouterLink>
            </li>
            <li class="nav-item">
              <RouterLink class="nav-link" to="/about">About</RouterLink>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>

  <h2>{{ header }}</h2>
  <form class="add-item-form" v-on:submit.prevent="saveItem()">
    <!-- <input
      v-model="newItem"
      v-on:keyup.enter="items.push({ id: items.length + 1, label: newItem })"
      type="text"
      placeholder="Add an item"
    /> -->
    <input v-model="newItem" type="text" placeholder="Add an item" />

    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      High Priority
    </label>
    <!-- <button
      class="btn btn-primary"
      v-on:click="items.push({ id: items.length + 1, label: newItem })"
    >
      Save Item
    </button> -->
    <button class="btn btn-primary">Save Item</button>

    <ul>
      <li v-for="item in items" v-bind:key="item.id">{{ item.label }}</li>
      <!-- <li v-for="{ id, label } in items" v-bind:key="id">{{ label }}</li> -->
    </ul>
  </form>
  <!-- <RouterView /> -->
</template>

<style scoped></style>
