# Employee Management App

A Vue 3 CRUD application for managing employees with Bootstrap styling and Axios-based API requests. The app includes create, read, update, and delete operations against a MockAPI endpoint.

## Features

- Add new employees
- Show employee list
- Update employee details
- Delete employees
- Responsive Bootstrap layout

## Project setup

```bash
npm install
```

## Development server

```bash
npm run serve
```

or

```bash
npm run dev
```

Then open `http://localhost:8080/` in your browser.

## Build for production

```bash
npm run build
```

## Linting

```bash
npm run lint
```

## Project structure

- `src/App.vue` — main layout and Bootstrap grid
- `src/main.js` — app bootstrap and Bootstrap CSS import
- `src/components/EmployeeForm.vue` — create employee form
- `src/components/EmployeeList.vue` — employee list view
- `src/components/UpdateEmployee.vue` — employee edit workflow
- `src/components/DeleteEmployee.vue` — delete employee table

## Notes

- Uses `axios` to communicate with `https://69e9b67515c7e2d512689a9a.mockapi.io/assignment`
- Bootstrap is loaded from `src/main.js`

## Repository

https://github.com/Varshith0708/WPAssignment-2
