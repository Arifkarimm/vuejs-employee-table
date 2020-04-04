<template>
  <div id="employee-table">
    <table>
      <tr v-for="employee in employees" :key="employee.id">
        <td>{{ employee.name }}</td>
        <td>{{ employee.email }}</td>
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