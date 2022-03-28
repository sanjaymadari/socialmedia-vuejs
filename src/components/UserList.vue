<template>
 <!-- <button @click="getUsers">Get Users</button> -->
 <table align="center" id="table">
  <tr>
   <th>SNo</th>
   <th>Username</th>
   <th>First Name</th>
   <th>Last Name</th>
   <th>Gender</th>
   <th>Mobile Number</th>
   <th>Email</th>
  </tr>
  <tr v-for="(user,i) in users" :key="user.username">
   <td>{{ i+1 }}</td>
   <td>{{ user.user_name }}</td>
   <td>{{ user.first_name }}</td>
   <td>{{ user.last_name }}</td>
   <td>{{ user.gender }}</td>
   <td>{{ user.mobile_number }}</td>
   <td>{{ user.email_id }}</td>
  </tr>
 </table>
    <h3 v-if="errorMsg">{{ errorMsg }}</h3>
</template>

<script>
import axios from 'axios'
export default {
  name: 'UserList',
  created () {
    this.getUsers()
  },
  data () {
    return {
      users: [],
      errorMsg: ''
    }
  },
  methods: {
    getUsers () {
      axios
        .get('http://172.40.43.210:5228/api/user')
        .then((response) => {
          console.log(response)
          this.users = response.data
        })
        .catch((error) => {
          console.log(error)
          this.errorMsg = 'Error retrieving data'
        })
    }
  }
}
</script>

<style scoped>
#table {
  font-family: Arial, Helvetica, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

#table td, #table th {
  border: 1px solid #ddd;
  padding: 8px;
}

#table tr:nth-child(even){background-color: #f2f2f2;}

#table tr:hover {background-color: #ddd;}

#table th {
  padding-top: 12px;
  padding-bottom: 12px;
  text-align: center;
  background-color: #04AA6D;
  color: white;
}
</style>
