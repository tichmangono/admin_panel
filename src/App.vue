<template>
  <div id="app">
    <div class="header">
      <h1>Recordtime Department Management</h1>
    </div>
     <button @click="showAddPopup = true">Add New</button>
    <DepartmentGrid :departments="departments" @edit-department="editDepartment" />

     <div v-if="showAddPopup" class="popup">
        <h3>Add New Department</h3>
        <form @submit.prevent="addDepartment">
          <div>
            <label for="addName">Department Name:</label>
            <input id="addName" v-model="newDepartment.name" required />
          </div>
          <div>
            <label for="addNumber">Department Number:</label>
            <input id="addNumber" v-model.number="newDepartment.number" />
          </div>
          <div>
            <label for="addLocation">Location:</label>
            <input id="addLocation" v-model="newDepartment.location" required />
          </div>
          <div>
            <label for="addActiveUsers">Active Users:</label>
            <input id="addActiveUsers" v-model.number="newDepartment.activeUsers" />
          </div>
          <button type="submit">Save</button>
          <button type="button" @click="showAddPopup = false">Cancel</button>
        </form>
      </div>
      <div v-if="showEditPopup" class="popup">
        <h3>Edit Department</h3>
        <form @submit.prevent="updateDepartment">
          <div>
            <label for="editName">Department Name:</label>
            <input id="editName" v-model="selectedDepartment.name" required />
          </div>
          <div>
            <label for="editNumber">Department Number:</label>
            <input id="editNumber" v-model.number="selectedDepartment.number" />
          </div>
          <div>
            <label for="editLocation">Location:</label>
            <input id="editLocation" v-model="selectedDepartment.location" required />
          </div>
          <div>
            <label for="editActiveUsers">Active Users:</label>
            <input id="editActiveUsers" v-model.number="selectedDepartment.activeUsers" />
          </div>
          <button type="submit">Save</button>
          <button type="button" @click="showEditPopup = false">Cancel</button>
        </form>
      </div>
  </div>
</template>

<script>
import DepartmentGrid from './components/DepartmentGrid.vue';

export default {
  components: {
    DepartmentGrid
  },
  methods: {
       addDepartment() {
      // Add validation here if necessary
      this.departments.push(this.newDepartment);
      this.newDepartment = {};
      this.showAddPopup = false;
    },
    updateDepartment() {
      // Update logic here
      this.showEditPopup = false;
    },
    editDepartment(department) {
      this.selectedDepartment = Object.assign({}, department);
      this.showEditPopup = true;
    },
    closePopup() {
      this.showAddPopup = false;
      this.showEditPopup = false;
    },

  },
  data() {
    return {
      showAddPopup: false,
      showEditPopup: false,
      selectedDepartment: null, // Used for editing
      newDepartment: {},
      departments: [
        {
          "name": "Cardiology",
          "number": 101,
          "location": "Rochester",
          "activeUsers": 25
        },
        {
          "name": "Neurology",
          "number": 102,
          "location": "Florida",
          "activeUsers": 18
        },
        {
          "name": "Oncology",
          "number": 103,
          "location": "Arizona",
          "activeUsers": 20
        },
        {
          "name": "Pediatrics",
          "number": 104,
          "location": "Rochester",
          "activeUsers": 22
        },
        {
          "name": "Dermatology",
          "number": 105,
          "location": "Florida",
          "activeUsers": 15
        },
        {
          "name": "Orthopedics",
          "number": 106,
          "location": "Arizona",
          "activeUsers": 30
        }
      ]
    };
  }
};
</script>

<style>
#app {
  font-family: Arial, Helvetica, sans-serif;
  color: #2c3e50;
  background-color: #f4f4f4;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.header {
  background-color: #007BFF;
  color: white;
  text-align: center;
  padding: 1em;
}
</style>
