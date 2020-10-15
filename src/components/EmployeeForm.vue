<template>
  <form id="employee-form" @submit.prevent="handleSubmit">
    <label>
      Employee name
      <input v-model="employee.name" type="text" />
    </label>
    <label>
      Employee email
      <input v-model="employee.email" type="text" />
    </label>
    <button>Add employee</button>
  </form>
</template>

<script>
export default {
  name: 'employee-form',
  data() {
    return {
      employee: { name: '', email: '' },
    };
  },
  methods: {
    handleSubmit() {
      this.$emit('add-employee', this.employee);
    },
  },
};
</script>

<style scoped>
form {
  margin-bottom: 2rem;
}
</style>
