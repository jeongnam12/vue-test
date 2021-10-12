<template>
  <div>
    <h1>사용자 정보를 입력하세요.</h1>
    <!-- <form name="user" method="get" action="/signUp"> -->
    <div class="input-row">
      <label for="password">이메일 주소: </label>
      <input
        type="email"
        name="email"
        id="email"
        placeholder="email을 입력해주세요"
      />
      <div class="input-row">
        <label for="password">패스워드: </label>
        <input
          type="password"
          name="password"
          id="password"
          placeholder="비밀번호를 입력해주세요"
        />
      </div>
    </div>
    <button type="submit" v-on:click="onSubmit">회원등록</button>
    <!-- </form> -->
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
  name: "SignUpForm",
  data: {},
  methods: {
    onSubmit: async () => {
      instance
        .post("insert", {
          email: "#email",
          password: "#password",
        })
        .then((res) => {
          alert(res);
        })
        .catch((err) => {
          alert(err);
        });
    },
  },
};
</script>
