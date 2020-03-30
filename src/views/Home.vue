<template>
    <div class="app">
      <div class="app-box">
        <Header />
        <Adduser v-on:add-user="AddUser" />
        <Users v-bind:users="users" v-on:delete-user="deleteUser" />
    </div>
    </div>
</template>

<script>

import axios from "axios";

import Header from "@/components/layout/Header";

import Users from "@/components/Users";

import Adduser from "@/components/addUser";

export default {
    name: "Home",
    components: {
        Header,
        Users,
        Adduser
    },
    data() {
        return {
            users: []
        };
    },

    methods: {
        deleteUser(id) {
          axios.delete(`https://jsonplaceholder.typicode.com/users/${id}`)
          // eslint-disable-next-line
          .then(res =>  this.users = this.users.filter(user => user.id !== id))
          .catch(err => console.log(err));
        },

        AddUser(newUser) {

          const { name } = newUser

           axios.post("https://jsonplaceholder.typicode.com/users", {
                name
            })
            // eslint-disable-next-line
            .then(res => this.users = [...this.users, newUser])
            .catch(err => console.log(err));
        }
        },
         created() {
            axios
                .get("https://jsonplaceholder.typicode.com/users?_limit=3")
                .then(res => (this.users = res.data))
                .catch(err => console.log(err));
    }
};
</script>


<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Open Sans", sans-serif;
}

.app {
  background-color: rgb(255, 255, 255);
  display: flex;
  justify-content: center;
}

.app-box {
  background:  #ffffff;
  width: 450px;
  height: 500px;
  overflow: auto;
  padding: 50px;
  box-shadow: 0 0 20px #d8d5d560;
  border-radius: 10px;
}

::-webkit-scrollbar {
    display: none;
}

</style>