<template>
  <div id="app">
    <!-- header -->
    <Header />
    <!-- 路由切换的容器 -->
    <router-view></router-view>
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/layout/Header";
export default {
  name: "app",
  data() {
    return {
      today: [],
    };
  },
  components: {
    Header,
  },
  mounted() {
    axios.get("http://jsonplaceholder.typicode.com/todos").then((res) => {
      this.today = res.data;
    });
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}
</style>
