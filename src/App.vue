<template>
  <div class="container">
    <h2>Employee Table</h2>
    <EmployeeFrom @add:employee="addEmployee" />
    <EmployeeTable :employees="employees" @del:employee="deleteEmployee" />
  </div>
</template>

<script>
import EmployeeTable from "@/components/EmployeeTable.vue";
import EmployeeFrom from "@/components/EmployeeFrom.vue";
export default {
  name: "App",
  data() {
    return {
      employees: [
        {
          id: 1,
          name: "Alexander Paul",
          email: "paul@gmail.com"
        },
        {
          id: 2,
          name: "John Doe",
          email: "doe@gmail.com"
        },
        {
          id: 3,
          name: "David Jack",
          email: "jack@gmail.com"
        }
      ]
    };
  },
  components: {
    EmployeeTable,
    EmployeeFrom
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
      this.employees = this.employees.filter(employee => employee.id !== id);
    }
  }
};
</script>

<style >
button {
  background: #009435;
  border: 1px solid #009435;
}

button:hover,
button:active,
button:focus {
  background: #32a95d;
  border: 1px solid #32a95d;
}

.small-container {
  max-width: 680px;
}
</style>