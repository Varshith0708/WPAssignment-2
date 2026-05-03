<template>
  <div class="container my-4">
    <div class="card panel-card h-100">
      <div class="card-header">
        <div class="d-flex align-items-center justify-content-between flex-wrap gap-3">
          <div>
            <h4 class="mb-1">Employee List</h4>
            <p class="text-muted small mb-0">View the latest records from the API.</p>
          </div>
          <span class="badge badge-soft-secondary">GET</span>
        </div>
      </div>
      <div class="card-body p-0">
        <div class="table-responsive table-custom">
          <table class="table mb-0">
            <thead>
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
