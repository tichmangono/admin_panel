<template>
  <div id="app">
    <DepartmentGrid :departments="departments" @add="addDepartment"></DepartmentGrid>
  </div>
</template>

<script>
import DepartmentGrid from './components/DepartmentGrid.vue';

export default {
  components: {
    DepartmentGrid
  },
  data() {
    return {
      departments: []
    };
  },
  mounted() {
    // Fetch initial departments (you would typically make an API call here)
    this.departments = [
      {
        name: 'HR',
        number: 101,
        location: 'Building A',
        activeUsers: 5
      },
      // Add more departments...
    ];
  },
  methods: {
    addDepartment(department) {
      this.departments.push(department);
    }
  }
};
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
