<template>
  <div class="table-container">
    <br/><br/>
    <button class="add-button" @click="addItem(department)">Add New Department</button>    
    <table class="department-table">
      <thead>
        <tr>
          <th>Department Name</th>
          <th>Department Number</th>
          <th>Location</th>
          <th>Active Users</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(department, index) in departments" :key="index">
          <td>{{ department.name }}</td>
          <td>{{ department.number }}</td>
          <td>{{ department.location }}</td>
          <td>{{ department.activeUsers }}</td>
          <td>
            <button class="edit-button" @click="editItem(department)">Edit</button>
            <button class="delete-button" @click="deleteItem(department)">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: ['departments'],
  methods: {
    addItem(department) {
      // Your edit logic here
      this.$emit('edit-department', department);      
      console.log("Add: ", department);
    },
    editItem(department) {
      // Your edit logic here
       this.$emit('edit-department', department);
      console.log("Edit: ", department);
    },
    deleteItem(department) {
      // Your delete logic here
      console.log("Delete: ", department);
    },
   

  },
};
</script>

<style scoped>
.table-container {
  overflow-x: auto;
}

.department-table {
  width: 100%;
  border-collapse: collapse;
  text-align: left;
  margin-top: 20px;
}

.department-table th,
.department-table td {
  padding: 12px 20px;
  border-bottom: 1px solid #ddd;
}

.department-table th {
  background-color: #007BFF;
  color: white;
}

.department-table tbody tr:hover {
  background-color: #f5f5f5;
}

.add-button,
.edit-button,
.delete-button {
  background-color: #007BFF;
  border: none;
  color: white;
  padding: 10px;
  margin: 5px;
  text-align: center;
  cursor: pointer;
  border-radius: 5px;
}
.add-button {
  background-color: #5cb85c;
}
.delete-button {
  background-color: #d9534f;
}
</style>
