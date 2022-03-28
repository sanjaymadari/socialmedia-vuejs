<template>
  <br>
  <button @click="getUser">Get User List</button>
  <button @click="createUser">Create User</button>
  <button @click="getPost">Get Post List</button>
  <button @click="createPost">Create Post</button>
  <div >
    <UserList v-if:="showUserList"/>
    <CreateUser v-if:="showCreateUser"/>
  </div>

</template>

<script>
import axios from 'axios'
import UserList from './components/UserList.vue'
import CreateUser from './components/CreateUser.vue'
export default {
  data () {
    return {
      users: [],
      errorMsg: '',
      showUserList: false,
      showCreateUser: false
    }
  },
  components: {
    UserList,
    CreateUser
  },
  methods: {
    onLoad () {
      axios.get('http://localhost:5228/api/user').then(response => {
        this.users = response.data
      }).catch((error) => {
        console.log(error)
        this.errorMsg = 'Error in fetching data'
      })
    },
    refreshData () {
      this.users = [{ username: 'sanju4', password: '1234' }, { username: 'sanju5', password: '1234' }]
    },
    getUser () {
      this.showUserList = true
      this.showCreateUser = false
    },
    createUser () {
      this.showUserList = false
      this.showCreateUser = true
    },
    getPost () {
      this.showUserList = false
      this.showCreateUser = false
    },
    createPost () {
      this.showUserList = false
      this.showCreateUser = false
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
button {
  background-color: #073621;
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  border-radius: 5em;
}
</style>
