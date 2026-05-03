<template>
  <div class="container my-4">
    <div class="card shadow-sm">
      <div class="card-header bg-danger text-white">
        <h4 class="mb-0">Delete Employee (axios DELETE)</h4>
      </div>
      <div class="card-body">
        <table class="table table-bordered table-hover">
          <thead class="table-danger">
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
                <button class="btn btn-danger btn-sm" @click="deleteItem(item.id)">Delete</button>
              </td>
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