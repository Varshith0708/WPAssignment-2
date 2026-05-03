<template>
  <div class="container my-4">
    <div class="card panel-card h-100">
      <div class="card-header">
        <div class="d-flex align-items-start justify-content-between flex-wrap gap-3">
          <div>
            <h4 class="mb-1">Update Employee</h4>
            <p class="text-muted small mb-0">Select an employee and update details instantly.</p>
          </div>
          <span class="badge badge-soft-warning">PUT</span>
        </div>
      </div>
      <div class="card-body">
        <div class="table-responsive table-custom mb-4">
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
                  <button class="btn btn-brand-warning btn-sm" @click="editItem(item)">Edit</button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>

        <div class="card panel-card" v-if="editData.id">
          <div class="card-body">
            <div class="d-flex align-items-center justify-content-between mb-3">
              <div>
                <h5 class="mb-1">Edit Employee</h5>
                <p class="text-muted small mb-0">Update the current employee record.</p>
              </div>
            </div>

            <div class="mb-3">
              <label class="form-label">Name</label>
              <input class="form-control" v-model="editData.name" placeholder="Name" />
            </div>

            <div class="mb-3">
              <label class="form-label">Designation</label>
              <input class="form-control" v-model="editData.designation" placeholder="Designation" />
            </div>

            <div class="mb-3">
              <label class="form-label">Department</label>
              <input class="form-control" v-model="editData.department" placeholder="Department" />
            </div>

            <div class="mb-3">
              <label class="form-label">Salary</label>
              <input class="form-control" type="number" v-model="editData.salary" placeholder="Salary" />
            </div>

            <div class="d-flex flex-wrap gap-2">
              <button class="btn btn-brand" @click="updateData">Update</button>
              <button class="btn btn-soft-secondary" @click="editData = { id: null }">Cancel</button>
            </div>
          </div>
        </div>

      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: "UpdateEmployee",
  data() {
    return {
      list: [],
      editData: {
        id: null,
        name: "",
        designation: "",
        department: "",
        salary: 0
      }
    }
  },
  methods: {
    async fetchData() {
      try {
        const resp = await axios.get('https://69e9b67515c7e2d512689a9a.mockapi.io/assignment');
        this.list = resp.data;
      } catch (err) {
        console.error(err);
      }
    },
    editItem(item) {
      this.editData = {
        id: item.id,
        name: item.name,
        designation: item.designation,
        department: item.department,
        salary: item.salary
      };
    },
    async updateData() {
      try {
        console.log("Updating ID:", this.editData.id);
        await axios.put(
          `https://69e9b67515c7e2d512689a9a.mockapi.io/assignment/${this.editData.id}`,
          this.editData
        );
        alert("Employee updated successfully!");
        this.fetchData();
        this.editData = { id: null, name: "", designation: "", department: "", salary: 0 };
      } catch (err) {
        console.error(err);
      }
    }
  },
  mounted() {
    this.fetchData();
  }
}
</script>
