<template>
  <div id="app" class="bg-light min-vh-100">
    <header class="bg-dark text-white text-center py-5 mb-4">
      <div class="container">
        <h1 class="display-5 fw-bold">Employee Management System</h1>
        <p class="lead text-secondary mx-auto" style="max-width: 720px;">
          CRUD Operations using Vue.js, Axios, and MockAPI
        </p>
      </div>
    </header>

    <div class="container">
      <div class="row gx-4 gy-4">
        <div class="col-12 col-lg-4">
          <EmployeeForm />
        </div>
        <div class="col-12 col-lg-8">
          <EmployeeList />
        </div>
        <div class="col-12 col-lg-6">
          <UpdateEmployee />
        </div>
        <div class="col-12 col-lg-6">
          <DeleteEmployee />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import EmployeeForm from './components/EmployeeForm.vue';
import EmployeeList from './components/EmployeeList.vue';
import UpdateEmployee from './components/UpdateEmployee.vue';
import DeleteEmployee from './components/DeleteEmployee.vue';

export default {
  name: 'App',
  components: {
    EmployeeForm,
    EmployeeList,
    UpdateEmployee,
    DeleteEmployee
  }
}
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  color: #2c3e50;
}
</style>