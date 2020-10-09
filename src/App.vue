<template>
  <div id="app">
    <img src="./assets/logo.png" />
    <ul>
      <li v-for="(item,index) in datas" :key="index">{{item.name}}</li>
    </ul>
    <HelloWorld />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";

export default {
  name: "App",
  data() {
    return {
      datas: []
    };
  },
  components: {
    HelloWorld
  },
  methods: {
    Fun() {
      //使用fetch方法
      // fetch("http://localhost:3000/js").then(res => {
      //   return res.json();
      // })
      // .then((data)=>{
      //     // console.log(data);
      //     this.datas = data;
      // })

      //使用axios方法
      this.$axios.get("http://localhost:3000").then(res => {
        console.log(res);
      });

      this.$axios
        .post("http://localhost:3000/js", { name: "js3", author: "lili" })
        .then(res => {
          console.log(res);
        });     
    }
  },
  mounted() {
    this.Fun();
  }
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
