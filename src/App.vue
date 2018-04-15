<template>
  <div id="app">
    <img src="./assets/logo.png">
    <HelloWorld/>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";

export default {
  name: "App",
  components: {
    HelloWorld
  },
  created() {
    
    let data = {
      username: "zhangsan",
      password: "123456"
    };
    /**@augments
     * 使用 fetch 请求
     */
    fetch("/apis/test/testToken.php", {
      method: "POST",
      headers: {
        "Content-type": "application/json",
        token: "f4c902c9ae5a2a9d8f84868ad064e706"
      },
      body: JSON.stringify(data)
    })
      .then(res => res.json())
      .then(data => {
        console.log(data);
      });

      /**@augments
       * axios 请求
       */

      this.$axios.post('/apis/test/testToken.php',data).then(res=>{
        console.log(res)
      })
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
