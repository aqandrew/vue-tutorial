<template>
  <div class="small-container">
    <h1>Employees</h1>

    <employee-table />
  </div>
</template>

<script>
import EmployeeTable from '@/components/EmployeeTable';

export default {
  name: 'app',
  components: {
    EmployeeTable,
  },
};
</script>

<style></style>
