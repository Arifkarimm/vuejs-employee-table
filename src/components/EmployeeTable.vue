<template>
  <div id="employee-table">
    <p v-if="employees.length < 1">No Employee</p>
    <table>
      <thead>
        <tr>
          <td>Name</td>
          <td>Email</td>
          <td>Action</td>
        </tr>
      </thead>
      <tr v-for="employee in employees" :key="employee.id">
        <td v-if="editting === employee.id">
          <input type="text" v-model="employee.name" />
        </td>
        <td v-else>{{ employee.name }}</td>
        <td v-if="editting === employee.id">
          <input type="text" v-model="employee.email" />
        </td>
        <td v-else>{{ employee.email }}</td>
        <td v-if="editting === employee.id">
          <button @click="editEmployee(employee)">Save</button>
          <button @click="editting = null">Cancel</button>
        </td>
        <td v-else>
          <button @click="editMode(employee.id)">Edit</button>
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
  },
  data() {
    return {
      editting: null
    };
  },
  methods: {
    editMode(id) {
      this.editting = id;
    },
    editEmployee(employee) {
      if (employee.name === "" || employee.email === "") {
        return;
      }
      this.$emit("edit:employee", employee.id, employee);
      this.editting = null;
    }
  }
};
</script>

<style>
button {
  margin: 0 0.5rem 0 0;
}

input {
  margin: 0;
}

.empty-table {
  text-align: center;
}
</style>