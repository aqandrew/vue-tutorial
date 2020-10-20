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

export default {
  name: 'app',
  components: {
    EmployeeTable,
    EmployeeForm,
  },
  data() {
    return {
      employees: [
        {
          id: 0,
          name: 'Valastalda',
          email: 'warlock@riseoftiamat.dnd',
        },
        {
          id: 1,
          name: 'Ornosti the Bloody',
          email: 'barbarian@riseoftiamat.dnd',
        },
        {
          id: 2,
          name: 'Pebble',
          email: 'bard@riseoftiamat.dnd',
        },
      ],
    };
  },
  methods: {
    addEmployee(employee) {
      const lastId =
        this.employees.length > 0
          ? this.employees[this.employees.length - 1].id
          : 0;
      const id = lastId + 1;
      const newEmployee = { ...employee, id };

      this.employees = [...this.employees, newEmployee];
    },
    deleteEmployee(id) {
      this.employees = this.employees.filter((employee) => employee.id !== id);
    },
    editEmployee(id, updatedEmployee) {
      this.employees = this.employees.map((employee) =>
        employee.id === id ? updatedEmployee : employee
      );
    },
  },
};
</script>

<style></style>
