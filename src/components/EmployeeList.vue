<template>
  <div class="container my-4">
    <div class="card shadow-sm">
      <div class="card-header bg-success text-white">
        <h4 class="mb-0">Employee List (axios GET)</h4>
      </div>
      <div class="card-body">
        <table class="table table-bordered table-hover">
          <thead class="table-success">
            <tr>
              <th>ID</th>
              <th>Name</th>
              <th>Designation</th>
              <th>Department</th>
              <th>Salary</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in list" :key="item.id">
              <td>{{ item.id }}</td>
              <td>{{ item.name }}</td>
              <td>{{ item.designation }}</td>
              <td>{{ item.department }}</td>
              <td>{{ item.salary }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: "EmployeeList",
  data() {
    return {
      list: []
    }
  },
  mounted() {
    axios.get('https://69e9b67515c7e2d512689a9a.mockapi.io/assignment')
      .then((resp) => {
        this.list = resp.data;
      })
      .catch(err => console.error(err));
  }
}
</script>