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

  <!-- <h1>{{ message }}</h1> -->
  <!-- <h1>{{ message ? message : "Welcome" }}</h1> -->
  <!-- <input v-model="message" /> -->
  <!-- <input v-model="message" /> -->
  <h2>{{ header }}</h2>
  <!-- <input v-model.lazy="newItem" type="text" placeholder="Add an item" />
  <input v-model.trim="newItem" type="text" placeholder="Add an item" />
  <input v-model.number="newItem" type="text" placeholder="Add an item" /> -->
  <input v-model.number="newItem" type="text" placeholder="Add an item" />
  {{ newItem }}
  <ul>
    <li v-for="item in items" v-bind:key="item.id">{{ item.label }}</li>
    <!-- <li v-for="{ id, label } in items" v-bind:key="id">{{ label }}</li> -->
  </ul>

  <!-- <RouterView /> -->
</template>

<style scoped></style>
