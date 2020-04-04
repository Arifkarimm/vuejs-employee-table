<template>
  <div id="employee-table">
    <table>
      <thead>
        <tr>
          <td>Name</td>
          <td>Email</td>
          <td>Action</td>
        </tr>
      </thead>
      <tr v-for="employee in employees" :key="employee.id">
        <td>{{ employee.name }}</td>
        <td>{{ employee.email }}</td>
        <td>
          <button>Edit</button>
          <button @click="$emit('del:employee', employee.id)">Delete</button>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "Employee-table",
  props: {
    employees: Array
  }
};
</script>

<style scoped>
</style>