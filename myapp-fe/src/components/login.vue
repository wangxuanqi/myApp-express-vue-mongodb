<template>
  <div class="container">
    <div class="main">
      <div class="contain">
        <div class="text">
          账号：
          <el-input
            placeholder="请输入内容"
            v-model="input"
            clearable>
          </el-input>
        </div>
        <div class="text">
          密码：
          <el-input placeholder="请输入密码" v-model="password" show-password></el-input>
        </div>
          <el-row type="flex" class="row-bg btn-contain" justify="space-around">
              <el-button @click="loginAuth" type="primary" round>登陆</el-button>
              <el-button type="primary" round>注册</el-button>
          </el-row>
      </div>
    </div>
    <div class="footer">power by wangxuanqi</div>
  </div>
</template>

<script>
    export default {
      name: "login",
      data() {
        return {
          input: '',
          password: ''
        }
      },
      methods: {
        loginAuth(){
          let user = {
            username: this.input,
            password: this.password
          } ;
          this.$http.post('/api/users/login', user)
            .then((response) => {
              if (response.status === 200 && response.data.auth) {
                this.$store.commit('setToken', response.data.token);
                console.log(response.data.msg)
              } else {
                console.log(response.data.msg)
              }
            })
            .catch((error) => {
              console.log(error)
            })
        }
      }
    }
</script>

<style scoped>
  .footer {
    background-color: #B3C0D1;
    color: #333;
    text-align: center;
    line-height: 150px;
  }
  .main {
    background-color: #E9EEF3;
    color: #333;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 600px;
  }

  body > .container {
    height: 800px;
  }
  .el-input{
    width: 300px;
  }
  .el-button{
    width: 100px;
  }
  .btn-contain{
    padding: 20px;
  }
  .contain{
    border: 1px solid #ebebeb;
    padding: 10px 30px;
    background-color: #fff;
  }
  .text{
    margin-top: 20px;
  }
</style>
