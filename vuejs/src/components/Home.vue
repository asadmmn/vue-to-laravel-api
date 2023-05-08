 <script setup>
import { onMounted } from "vue";
import useStudent from "../composables/studentApi";
const { studentData, error, getAllStudent } = useStudent();
onMounted(getAllStudent);
</script>
<template>
<main>
  <h1>Asad's full stack app Api's</h1>
  <div v-if="error">Oops! Error encountered: {{ error.message }}</div>
  <table v-else-if="studentData">
    <thead>
      <tr>
        <th>#</th>
        <th>Name</th>
        <th>Email</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="({ id, stuname, email }, i) in studentData" :key="id">
        <td>{{ ++i }}</td>
        <td>{{ stuname }}</td>
        <td>{{ email }}</td>
      </tr>
    </tbody>
  </table>
  </main>
</template>


<style scoped>
main{
  justify-content:center;
  text-align:center;
background-color:gray;
border-radius:8px;
}
main h1{
  background-color:tan;
}
table {
  justify-content:center;
  margin: auto;
  padding: 20px;
  background-color: tan;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 18px;
  color: #333;
  line-height: 1.5;
}

thead th {
  background-color: #ccc;
  font-weight: bold;
}

tbody tr {
  background-color: #f2f2f2;
}
</style>
