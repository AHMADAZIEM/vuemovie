<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png" /> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    <input type="text" v-model="user" />
    <button type="button" @click="addUser" class="btn btn-primary ml-2">
      Add
    </button>
    <!-- <ListUser @deleteObject="removeUser" :users="users" /> -->
    <table class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Name</th>
          <th scope="col">Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(user, index) in users" :key="index">
          <th scope="row">{{ index + 1 }}</th>
          <td>{{ user.first_name }} {{ user.last_name }}</td>
          <td>
            <button
              type="button"
              @click="removeUser(index)"
              class="btn btn-danger"
            >
              Remove
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
// import ListUser from "../components/ListUser";
import axios from "axios";

export default {
  name: "Home",
  components: {
    // HelloWorld
    // ListUser
  },
  data() {
    return {
      users: [],
      user: ""
    };
  },
  created() {
    this.getUsers();
  },
  methods: {
    getUsers() {
      axios.get("https://reqres.in/api/users?page=2").then(response => {
        // console.log("response ", response.data.data);
        this.users = response.data.data;
        console.log("users ", this.users);
      });
    },
    addUser() {
      this.users.push(this.user);
    },
    removeUser(index) {
      // alert('Data from child ' + index)
      // console.log(index);
      this.users.splice(index, 1);
    }
  }
};
</script>
