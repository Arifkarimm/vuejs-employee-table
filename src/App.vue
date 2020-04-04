<template>
  <div class="container">
    <h2>Employee Table</h2>
    <EmployeeFrom @add:employee="addEmployee" />
    <EmployeeTable :employees="employees" />
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
    }
  }
};
</script>

<style scoped>
</style>