<template>
  <div class="container my-4">
    <div class="card panel-card h-100">
      <div class="card-header">
        <div class="d-flex align-items-start justify-content-between flex-wrap gap-3">
          <div>
            <h4 class="mb-1">Create Employee</h4>
            <p class="text-muted small mb-0">Add a new employee record instantly.</p>
          </div>
          <span class="badge badge-soft-primary">POST</span>
        </div>
      </div>
      <div class="card-body">
        <form @submit="postData">

          <div class="mb-3">
            <label class="form-label">Name</label>
            <input type="text" class="form-control" placeholder="Enter name" v-model="employee.name" />
          </div>

          <div class="mb-3">
            <label class="form-label">Designation</label>
            <input type="text" class="form-control" placeholder="Enter designation" v-model="employee.designation" />
          </div>

          <div class="mb-3">
            <label class="form-label">Department</label>
            <input type="text" class="form-control" placeholder="Enter department" v-model="employee.department" />
          </div>

          <div class="mb-3">
            <label class="form-label">Salary</label>
            <input type="number" class="form-control" placeholder="Enter salary" v-model="employee.salary" />
          </div>

          <button type="submit" class="btn btn-brand w-100 mt-2">Add Employee</button>

        </form>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: "EmployeeForm",
  data() {
    return {
      employee: {
        name: null,
        designation: null,
        department: null,
        salary: 0
      }
    }
  },
  methods: {
    postData(e) {
      axios.post("https://69e9b67515c7e2d512689a9a.mockapi.io/assignment", {
        name: this.employee.name,
        designation: this.employee.designation,
        department: this.employee.department,
        salary: this.employee.salary
      })
      .then(res => {
        console.log(res.data);
        alert("Employee added successfully!");
        this.employee = { name: null, designation: null, department: null, salary: 0 };
      })
      .catch(err => console.log(err));

      e.preventDefault();
    }
  }
}
</script>