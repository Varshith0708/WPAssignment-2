<template>
  <div id="app" class="app-shell">
    <nav class="navbar navbar-expand-lg navbar-dark py-3 shadow-none">
      <div class="container">
        <a class="navbar-brand fw-bold title-link" href="#">WPAssignment 2</a>
        <div class="d-flex align-items-center gap-2">
          <span class="badge badge-pill badge-soft-primary">Vue 3</span>
          <span class="badge badge-pill badge-soft-secondary">Axios</span>
        </div>
      </div>
    </nav>

    <header class="hero-section py-5">
      <div class="container">
        <div class="row align-items-center gy-4">
          <div class="col-lg-7">
            <p class="eyebrow mb-3">Premium employee dashboard</p>
            <h1 class="hero-title mb-4">A modern, productive interface for employee management.</h1>
            <p class="hero-copy text-muted mb-4">
              Keep your existing API integration and component logic while enjoying a polished responsive experience.
            </p>
            <div class="d-flex flex-wrap gap-2">
              <span class="badge badge-pill badge-soft-primary">Modern interface</span>
              <span class="badge badge-pill badge-soft-secondary">Clean data tables</span>
              <span class="badge badge-pill badge-soft-muted">Responsive layout</span>
            </div>
          </div>
          <div class="col-lg-5">
            <div class="hero-card p-4 shadow-lg">
              <div class="d-flex justify-content-between align-items-start mb-3">
                <div>
                  <p class="small text-muted mb-1">Live API status</p>
                  <h3 class="mb-0">Connected</h3>
                </div>
                <span class="badge badge-pill badge-soft-primary">Active</span>
              </div>
              <p class="small text-secondary mb-3">
                All operations are executed through the connected MockAPI backend without modifying existing logic.
              </p>
              <div class="d-flex gap-3 flex-wrap">
                <div class="status-chip">
                  <strong>4</strong>
                  <span>Views</span>
                </div>
                <div class="status-chip">
                  <strong>2</strong>
                  <span>Actions</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </header>

    <main class="container pb-5">
      <div class="row gx-4 gy-4">
        <div class="col-12 col-xl-4">
          <EmployeeForm />
        </div>
        <div class="col-12 col-xl-8">
          <EmployeeList />
        </div>
        <div class="col-12 col-lg-6">
          <UpdateEmployee />
        </div>
        <div class="col-12 col-lg-6">
          <DeleteEmployee />
        </div>
      </div>
    </main>

    <footer class="footer-section py-4">
      <div class="container text-center">
        <p class="mb-1 text-muted">Built with Vue 3, Axios and Bootstrap.</p>
        <small class="text-secondary">Existing backend integration and component logic remain unchanged.</small>
      </div>
    </footer>
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
:root {
  --surface-0: #f6f9ff;
  --surface-1: #ffffff;
  --surface-2: rgba(255, 255, 255, 0.86);
  --surface-strong: #ffffff;
  --text-primary: #0f172a;
  --text-secondary: #475569;
  --text-muted: #64748b;
  --brand-primary: #4f46e5;
  --brand-secondary: #2563eb;
  --accent: #0ea5e9;
  --border: rgba(15, 23, 42, 0.08);
  --shadow-soft: 0 24px 64px rgba(15, 23, 42, 0.08);
}

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  min-height: 100vh;
  background: #eff6ff;
  color: var(--text-primary);
}

#app {
  min-height: 100vh;
  background: radial-gradient(circle at top left, rgba(79, 63, 212, 0.18), transparent 24%),
    radial-gradient(circle at bottom right, rgba(37, 99, 235, 0.14), transparent 22%),
    linear-gradient(180deg, #f8fbff 0%, #eff6ff 100%);
}

.navbar {
  background: transparent;
}

.title-link {
  color: #ffffff;
  letter-spacing: 0.05em;
}

.hero-section {
  background: linear-gradient(140deg, rgba(59, 130, 246, 0.95), rgba(15, 23, 42, 0.95));
  border-radius: 32px;
  margin: 0 1rem;
  padding: 2.5rem 2rem;
}

.hero-title {
  font-size: clamp(2.5rem, 4vw, 3.5rem);
  line-height: 1.05;
  color: #ffffff;
}

.eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  color: #c7d2fe;
  font-size: 0.85rem;
  text-transform: uppercase;
  letter-spacing: 0.18em;
}

.hero-copy {
  max-width: 680px;
  color: rgba(248, 250, 252, 0.88);
}

.hero-card {
  border-radius: 24px;
  background: rgba(255, 255, 255, 0.92);
  border: 1px solid rgba(255, 255, 255, 0.6);
}

.status-chip {
  min-width: 132px;
  padding: 1rem;
  border-radius: 18px;
  background: rgba(79, 70, 229, 0.08);
  color: var(--text-primary);
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
}

.footer-section {
  background: rgba(15, 23, 42, 0.04);
  margin: 0 1rem 1rem;
  border-radius: 24px;
}

.badge-soft-primary,
.badge-soft-secondary,
.badge-soft-muted {
  font-size: 0.75rem;
  padding: 0.65rem 0.9rem;
  border-radius: 999px;
}

.badge-soft-primary {
  background: rgba(79, 70, 229, 0.12);
  color: #4338ca;
}

.badge-soft-secondary {
  background: rgba(37, 99, 235, 0.12);
  color: #1d4ed8;
}

.badge-soft-muted {
  background: rgba(71, 85, 105, 0.12);
  color: #475569;
}

.panel-card {
  border-radius: 28px;
  border: 1px solid var(--border);
  background: rgba(255, 255, 255, 0.96);
  box-shadow: var(--shadow-soft);
}

.panel-card .card-header {
  background: transparent;
  border-bottom: none;
  padding-bottom: 0;
}

.panel-card .card-body {
  padding-top: 1rem;
}

.panel-card .card-title {
  font-weight: 700;
  letter-spacing: -0.03em;
}

.table-custom {
  border-radius: 22px;
  overflow: hidden;
  background: #ffffff;
  box-shadow: 0 18px 42px rgba(15, 23, 42, 0.06);
}

.table-custom thead th {
  background: rgba(79, 70, 229, 0.08);
  color: #334155;
  border: none;
  font-weight: 700;
}

.table-custom tbody tr {
  transition: background-color 0.25s ease;
}

.table-custom tbody tr:hover {
  background: rgba(79, 70, 229, 0.045);
}

.table-custom td,
.table-custom th {
  border: none;
  vertical-align: middle;
}

.btn-brand,
.btn-brand-warning,
.btn-soft-secondary,
.btn-soft-danger {
  border-radius: 14px;
  padding: 0.85rem 1.35rem;
  transition: transform 0.2s ease, box-shadow 0.2s ease, background-color 0.2s ease;
}

.btn-brand {
  background: linear-gradient(135deg, #4f46e5, #0ea5e9);
  color: #ffffff;
  box-shadow: 0 18px 40px rgba(79, 70, 229, 0.18);
}

.btn-brand:hover {
  transform: translateY(-1px);
  background: linear-gradient(135deg, #4338ca, #0284c7);
}

.btn-brand-warning {
  background: #fbbf24;
  color: #0f172a;
}

.btn-brand-warning:hover {
  background: #f59e0b;
}

.btn-soft-secondary {
  background: rgba(37, 99, 235, 0.12);
  color: #1d4ed8;
}

.btn-soft-secondary:hover {
  background: rgba(37, 99, 235, 0.18);
}

.btn-soft-danger {
  background: rgba(239, 68, 68, 0.12);
  color: #b91c1c;
}

.btn-soft-danger:hover {
  background: rgba(239, 68, 68, 0.2);
}

.form-control {
  border-radius: 14px;
  border: 1px solid rgba(15, 23, 42, 0.12);
  background: #f8fbff;
  padding: 1rem 1.05rem;
  transition: border-color 0.2s ease, box-shadow 0.2s ease;
}

.form-control:focus {
  border-color: rgba(79, 70, 229, 0.5);
  box-shadow: 0 0 0 0.2rem rgba(99, 102, 241, 0.15);
}

.form-label {
  font-weight: 600;
  color: #334155;
}

.card-header .card-title {
  font-size: 1.1rem;
  color: #0f172a;
}

.card-header .text-white {
  color: #0f172a !important;
}

.card-header.bg-primary,
.card-header.bg-success,
.card-header.bg-warning,
.card-header.bg-danger {
  background: transparent !important;
}

.card-header.bg-primary h4,
.card-header.bg-success h4,
.card-header.bg-warning h4,
.card-header.bg-danger h4 {
  color: #0f172a;
}

@media (max-width: 991.98px) {
  .hero-section {
    margin: 0 0.5rem;
    padding: 2rem 1.5rem;
  }

  .footer-section {
    margin: 0 0.5rem 1rem;
  }
}

@media (max-width: 767.98px) {
  .hero-title {
    font-size: 2.2rem;
  }

  .status-chip {
    min-width: 100%;
  }
}
</style>
