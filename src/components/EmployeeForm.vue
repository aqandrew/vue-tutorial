<template>
  <form id="employee-form" @submit.prevent="handleSubmit">
    <label>
      Employee name
      <input
        type="text"
        v-model="employee.name"
        :class="{ 'has-error': submitting && invalidName }"
        @focus="clearStatus"
        @keypress="clearStatus"
        ref="first"
      />
    </label>
    <label>
      Employee email
      <input
        type="text"
        v-model="employee.email"
        :class="{ 'has-error': submitting && invalidEmail }"
        @focus="clearStatus"
      />
    </label>
    <p v-if="error && submitting" class="error-message">
      ❗ Please fill out all required fields
    </p>
    <p v-if="success" class="success-message">✅ Employee successfully added</p>
    <button>Add employee</button>
  </form>
</template>

<script>
export default {
  name: 'employee-form',
  data() {
    return {
      submitting: false,
      error: false,
      success: false,
      employee: { name: '', email: '' },
    };
  },
  computed: {
    invalidName() {
      return this.employee.name === '';
    },
    invalidEmail() {
      return this.employee.email === '';
    },
  },
  methods: {
    handleSubmit() {
      this.submitting = true;
      this.clearStatus;

      if (this.invalidName || this.invalidEmail) {
        this.error = true;
        return;
      }

      this.$emit('add-employee', this.employee);
      this.$refs.first.focus();
      this.employee = { name: '', email: '' };
      this.error = false;
      this.success = true;
      this.submitting = false;
    },
    clearStatus() {
      this.success = false;
      this.error = false;
    },
  },
};
</script>

<style scoped>
form {
  margin-bottom: 2rem;
}

[class*='-message'] {
  font-weight: 500;
}

.error-message {
  color: #d33c40;
}

.success-message {
  color: #32a95d;
}
</style>
