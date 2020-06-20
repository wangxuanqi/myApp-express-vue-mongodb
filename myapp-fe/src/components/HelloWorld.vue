<template>
  <div class="HelloWorld">
    欢迎来到王宣淇的主页
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      count: 0
    }
  },
  methods: {
    getD () {
      let that = this;
      this.http.get("/api/users/user")
        .then(function(response){
          document.getElementById("data").innerHTML = that.msg+" "+response.data;
          console.log(response);
        })
        .catch(function(error){
          console.log(error);
        })
    },
    increment () {
      console.log(this.msg);
      this.count++;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .HelloWorld{
    font-size: 50px;
    text-align: center;
    line-height: 500px;
  }
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
