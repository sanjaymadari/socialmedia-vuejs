<template>
  <h2>{{name}}</h2>
  <div>
  <form @submit.prevent="createUser">
    <input type="text" id="username" name="username" placeholder="Enter Username" v-model="formData.user_name">
    <input type="text" id="firstname" name="firstname" placeholder="Enter First Name" v-model="formData.first_name">
    <input type="text" id="lastname" name="lastname" placeholder="Enter Last Name" v-model="formData.last_name">
    <input type="text" id="dateofbirth" name="dateofbirth" placeholder="Enter Date Of Birth" v-model="formData.date_of_birth">
    <input type="text" id="gender" name="gender" placeholder="Enter Gender" v-model="formData.gender">
    <!-- <select id="gender" name="gender">
      <option>Select Gender</option>
      <option value="Male">Male</option>
      <option value="Female">Female</option>
    </select> -->
    <input type="email" id="email" name="email" placeholder="Enter Email" v-model="formData.email_id">
    <input type="text" id="contact" name="mobilenumber" placeholder="Enter Contact" v-model="formData.mobile_number">
    <input type="password" id="password" name="password" placeholder="Enter Password" v-model="formData.password">
    <input type="password" id="cpassword" name="cpassword" placeholder="Confirm Password">
    <button>Create User</button>
    <!-- <input type="submit" value="Submit"> -->
  </form>
</div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'CreateUser',
  data () {
    return {
      name: 'Create User',
      formData: {
        user_name: '',
        first_name: '',
        last_name: '',
        date_of_birth: '',
        gender: '',
        email_id: '',
        mobile_number: '',
        password: ''
      }
    }
  },
  methods: {
    createUser () {
      axios.post('http://172.40.43.210:5228/api/user', this.formData).then((response) => {
        console.log(response)
      }).catch((error) => {
        console.log(error)
      })
    }
  }
}
</script>

<style scoped>
input[type=text], input[type=password], input[type=email], input[type=number], select {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

input[type=submit] {
  width: 100%;
  background-color: #4CAF50;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type=submit]:hover {
  background-color: #45a049;
}

div {
  margin: auto;
  width: 30%;
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
}
</style>
