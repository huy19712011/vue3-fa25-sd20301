<script setup>
import List from "@/components/student/List.vue";
import { ref } from "vue";

const students = ref([
  { id: 1, name: "A", email: "a@gmail.com", phone: "111111" },
  { id: 2, name: "B", email: "b@gmail.com", phone: "222222" },
]);
</script>

<template>
  <div class="container">
    <List :students="students"></List>
  </div>
</template>
