<template>
  <div id="employee-form">
    <form @submit.prevent="handleEmployee">
      <label>Employee Name</label>
      <input type="text" v-model="employee.name" />
      <label>Employee Email</label>
      <input type="text" v-model="employee.email" />
      <button>Add Employee</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "Employee-form",
  data() {
    return {
      employee: {
        name: "",
        email: ""
      }
    };
  },
  methods: {
    handleEmployee() {
      this.$emit("add:employee", this.employee);
    }
  }
};
</script>

<style scoped>
</style>