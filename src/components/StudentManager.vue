<script setup>
import { ref } from "vue";

const students = ref([
  { id: 1, name: "A", email: "a@gmail.com", phone: "111111" },
  { id: 2, name: "B", email: "b@gmail.com", phone: "222222" },
]);

const isEditing = ref(false);

const form = ref({
  id: null,
  name: "",
  email: "",
  phone: "",
});

function handleSubmit() {
  if (isEditing.value) {
    updateStudent();
  } else {
    addStudent();
  }
}

function addStudent() {
  students.value.push({
    id: students.value.length + 1,
    name: form.value.name,
    email: form.value.email,
    phone: form.value.phone,
  });

  resetForm();
}

function editStudent(student) {
  isEditing.value = true;
  form.value = { ...student };
}

function resetForm() {
  form.value = { id: null, name: "", email: "", phone: "" };
}

function updateStudent() {
  const index = students.value.findIndex((s) => s.id === form.value.id);
  students.value[index] = { ...form.value };

  resetForm();
  isEditing.value = false;
}

function cancelEdit() {
  resetForm();
  isEditing.value = false;
}

function deleteStudent(id) {
  students.value = students.value.filter((s) => s.id !== id);
}
</script>

<template>
  <div class="container">
    <form @submit.prevent="handleSubmit()" class="form">
      <input v-model="form.name" placeholder="Name" required />
      <input v-model="form.email" placeholder="Email" required />
      <input v-model="form.phone" placeholder="Phone" required />
      <button type="submit">{{ isEditing ? "Update" : "Add" }}</button>
      <button v-if="isEditing" type="button" @click="cancelEdit()">Cancel</button>
    </form>

    <table border="1" cellpadding="6" style="width: 100%">
      <thead>
        <tr>
          <th>Id</th>
          <th>Name</th>
          <th>Email</th>
          <th>Phone</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="student in students" :key="student.id">
          <td>{{ student.id }}</td>
          <td>{{ student.name }}</td>
          <td>{{ student.email }}</td>
          <td>{{ student.phone }}</td>
          <td>
            <button @click="editStudent(student)">Edit</button>
            <button @click="deleteStudent(student.id)">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped>
.container {
  width: 600px;
  margin: auto;
}
form {
  margin-bottom: 20px;
  display: flex;
  flex-direction: column;
  gap: 8px;
  flex-wrap: wrap;
}
input {
  padding: 6px;
}
button {
  padding: 6px 32px;
}
</style>
