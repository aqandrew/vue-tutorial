<template>
  <div class="small-container">
    <h1>Employees</h1>

    <employee-table :employees="employees" />
  </div>
</template>

<script>
import EmployeeTable from '@/components/EmployeeTable';

export default {
  name: 'app',
  components: {
    EmployeeTable,
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
};
</script>

<style></style>
