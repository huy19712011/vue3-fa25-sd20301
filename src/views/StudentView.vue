<script setup>
import Create from "@/components/student/Create.vue";
import Edit from "@/components/student/Edit.vue";
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

const model = ref({
  student: {
    id: "",
    name: "",
    email: "",
    phone: "",
  },
});

const editStudent = (student) => {
  model.value.student = { ...student };
};

const updateStudent = (student) => {
  const index = students.value.findIndex((s) => s.id === student.id);
  if (index !== -1) {
    students.value[index] = { ...student };
  }

  model.value.student = {
    id: "",
    name: "",
    email: "",
    phone: "",
  };
};

const deleteStudent = (student) => {
  students.value = students.value.filter((s) => s.id !== student.id);
};
</script>

<template>
  <div class="container">
    <Create @add-student="addStudent"></Create>
    <List :students="students" @edit-student="editStudent" @delete-student="deleteStudent"></List>
    <Edit :student="model.student" @update-student="updateStudent"></Edit>
  </div>
</template>
