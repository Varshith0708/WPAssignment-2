<template>
  <div class="container my-4">
    <div class="card shadow-sm">
      <div class="card-header bg-warning text-dark">
        <h4 class="mb-0">Update Employee (axios PUT)</h4>
      </div>
      <div class="card-body">
        <table class="table table-bordered table-hover">
          <thead class="table-warning">
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
                <button class="btn btn-warning btn-sm" @click="editItem(item)">Edit</button>
              </td>
            </tr>
          </tbody>
        </table>

        <!-- Edit Section -->
        <div class="card mt-4 border-warning" v-if="editData.id">
          <div class="card-header bg-warning text-dark">
            <h5 class="mb-0">Edit Employee</h5>
          </div>
          <div class="card-body">

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

            <button class="btn btn-success" @click="updateData">Update</button>
            <button class="btn btn-secondary ms-2" @click="editData = { id: null }">Cancel</button>
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