<script setup>
import Create from "@/components/student/Create.vue";
import List from "@/components/student/List.vue";
import { ref } from "vue";

const students = ref([
  { id: 1, name: "A", email: "a@gmail.com", phone: "111111" },
  { id: 2, name: "B", email: "b@gmail.com", phone: "222222" },
]);

const addStudent = (student) => {
  student.id = students.value.length + 1;

  students.value.push(student);
};
</script>

<template>
  <div class="container">
    <Create @add-student="addStudent"></Create>
    <List :students="students"></List>
  </div>
</template>
