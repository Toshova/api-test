<template>
  <div>
    <table id="users">
  <tr>
    <th>Name</th>
    <th>E-mail</th>
    <th>City</th>
  </tr>
  <tr v-for="user in users" :key="user.id">
    <td>{{ user.name }}</td>
    <td>{{ user.email }}</td>
    <td>{{ user.address.city }}</td>
  </tr>

</table>

  </div>
  


</template>



<script>

export default {
  name: 'IndexPage',
  data() {
    return {
      users: [],
    };
  },
  mounted() {
    this.$axios.get('https://jsonplaceholder.typicode.com/users')
    .then(response => (this.users = response.data))
    .catch(error => console.log(error));
  },
}

</script>



<style scoped>

#users {
  font-family: Arial, Helvetica, sans-serif;
  border-collapse: collapse;
  margin-top: 20px;
  width: 100%;
}

#users td, #users  th {
  border: 1px solid #ddd;
  padding: 8px;
  
}

#users tr:nth-child(even){background-color: #f2f2f2;}

#users tr:hover {background-color: #ddd;}

#users th {
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: left;
  background-color: #04AA6D;
  color: white;
  
}
</style>