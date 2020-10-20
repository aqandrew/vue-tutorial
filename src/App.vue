<template>
  <div class="small-container">
    <h1>Employees</h1>

    <employee-form @add-employee="addEmployee" />
    <employee-table
      :employees="employees"
      @delete-employee="deleteEmployee"
      @edit-employee="editEmployee"
    />
  </div>
</template>

<script>
import EmployeeTable from '@/components/EmployeeTable';
import EmployeeForm from '@/components/EmployeeForm';

const API_URL = 'https://jsonplaceholder.typicode.com/users';

export default {
  name: 'app',
  components: {
    EmployeeTable,
    EmployeeForm,
  },
  data() {
    return {
      employees: [],
    };
  },
  mounted() {
    this.getEmployees();
  },
  methods: {
    async addEmployee(employee) {
      const response = await fetch(API_URL, {
        method: 'POST',
        body: JSON.stringify(employee),
        headers: { 'Content-type': 'application/json; charset=UTF-8' },
      });
      const data = await response.json();

      this.employees = [...this.employees, data];
    },
    deleteEmployee(id) {
      this.employees = this.employees.filter((employee) => employee.id !== id);
    },
    editEmployee(id, updatedEmployee) {
      this.employees = this.employees.map((employee) =>
        employee.id === id ? updatedEmployee : employee
      );
    },
    async getEmployees() {
      try {
        const response = await fetch(API_URL);
        const data = await response.json();

        this.employees = data;
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>

<style></style>
