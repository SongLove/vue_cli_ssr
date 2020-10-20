<template>
  <div id="app">
    <router-link to="/">首页</router-link>
    <router-link to="/about">关于</router-link>
    <img src="./assets/logo.png">
    <div
      v-for="(item, index) in figure"
      :key="index"
    >
      <p>{{item.genre}}</p>
      <p>{{item.name}}</p>
      <p>{{item.lang}}</p>
      <p>{{item.language}}</p>
      <img :src="item.poster"/>
      <p>{{item.description}}</p>
      <p>{{item.country}}</p>
    </div>
    <router-view />
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "App",
  data() {
    return {
      figure: [],
    };
  },
  created() {
    axios.get("https://movie.querydata.org/api?id=1302425").then(({ data }) => {
      this.figure = data.data;
    });
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
