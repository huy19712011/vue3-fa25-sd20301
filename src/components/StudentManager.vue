<script setup>
import { ref } from "vue";

const students = ref([
  { id: 1, name: "A", email: "a@gmail.com", phone: "111111" },
  { id: 2, name: "B", email: "b@gmail.com", phone: "222222" },
]);

const form = ref({
  id: null,
  name: "",
  email: "",
  phone: "",
});

function addStudent() {
  students.value.push({
    id: students.value.length + 1,
    name: form.value.name,
    email: form.value.email,
    phone: form.value.phone,
  });
}
</script>

<template>
  <div class="container">
    <form @submit.prevent="addStudent()" class="form">
      <input v-model="form.name" placeholder="Name" required />
      <input v-model="form.email" placeholder="Email" required />
      <input v-model="form.phone" placeholder="Phone" required />
      <button>Add</button>
      <button>Cancel</button>
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
            <button>Edit</button>
            <button>Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped></style>
