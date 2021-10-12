//src/components/Login.vue

<template>
  <div>
    <h2>Log In</h2>
    <!-- <form @submit="onSubmit"> -->
    <input placeholder="Enter your ID" v-model="uid" />
    <input placeholder="Enter your password" v-model="password" />
    <button type="submit" v-on:click="onSubmit">Login</button>
    <!-- </form> -->
    <br />
    <router-link to="/SignUp">회원가입</router-link>
  </div>
</template>

<script>
import axios from "axios";
const instance = axios.create({
  baseURL: "http://localhost:3000/",
  withCredentials: false,
  headers: {
    "Access-Control-Allow-Origin": "*",
    "Access-Control-Allow-Methods": "GET,PUT,POST,DELETE,PATCH,OPTIONS",
  },
});

export default {
  name: "Login",
  data: () => ({
    uid: "",
    password: "",
  }),

  methods: {
    onSubmit: async () => {
      instance
        .post("login", {
          email: "234234",
          password: "432432",
        })
        .then((res) => {
          alert(res.data);
        })
        .catch((err) => {
          alert(err);
        });
    },
  },
};
</script>
