<template>
  <div class="container my-4">
    <div class="card panel-card h-100">
      <div class="card-header">
        <div class="d-flex align-items-start justify-content-between flex-wrap gap-3">
          <div>
            <h4 class="mb-1">Delete Employee</h4>
            <p class="text-muted small mb-0">Remove records from the API safely.</p>
          </div>
          <span class="badge badge-soft-danger">DELETE</span>
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
                <th>Action</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="item in list" :key="item.id">
                <td>{{ item.id }}</td>
                <td>{{ item.name }}</td>
                <td>{{ item.designation }}</td>
                <td>{{ item.department }}</td>
                <td>{{ item.salary }}</td>
                <td>
                  <button class="btn btn-soft-danger btn-sm" @click="deleteItem(item.id)">Delete</button>
                </td>
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
  name: "DeleteEmployee",
  data() {
    return {
      apiURL: "https://69e9b67515c7e2d512689a9a.mockapi.io/assignment",
      list: []
    };
  },
  methods: {
    async fetchData() {
      try {
        const res = await axios.get(this.apiURL);
        this.list = res.data;
      } catch (err) {
        console.error("Fetch Error:", err);
      }
    },
    async deleteItem(id) {
      if (!confirm("Are you sure you want to delete this employee?")) return;
      try {
        await axios.delete(`${this.apiURL}/${id}`);
        this.list = this.list.filter(item => item.id !== id);
        alert("Employee deleted successfully!");
      } catch (err) {
        console.error("Delete Error:", err);
      }
    }
  },
  mounted() {
    this.fetchData();
  }
};
</script>
