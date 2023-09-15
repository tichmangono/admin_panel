<template>
 <div>
  <!-- Add your search and select logic here -->
  <button @click="$emit('closePopup')">Close</button>
 </div>
</template>

<script>
export default {
 methods: {
  selectDepartment(department) {
   this.$emit('addDepartment', department);
   this.$emit('closePopup');
  }
 }
};
</script>

<style>
h3 {
 margin: 40px 0 0;
}

ul {
 list-style-type: none;
 padding: 0;
}

li {
 display: inline-block;
 margin: 0 10px;
}

a {
 color: #42b983;
}
</style>