<template>
  <div id="app">
    <div class="header">
      <div class="right-header">
        <el-menu
          default-active="activeIndex"
          class="el-menu-demo"
          mode="horizontal"
          @select="handleSelect"
          text-color="#000"
          router
          active-text-color="#66b1ff">
          <el-menu-item index="1">处理中心</el-menu-item>
          <el-menu-item index="2">我的工作台</el-menu-item>
          <el-menu-item index="3">消息中心</el-menu-item>
          <el-menu-item index="Login">登陆</el-menu-item>
        </el-menu>
      </div>
    </div>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      activeIndex: 1
    }
  },
  methods: {
    handleSelect(key, keyPath) {
      console.log(key, keyPath);
    }
  }

}
</script>

<style>
#app {

}


.right-header{
  float: right;
}

.header {
  position: relative;
  background-color: #fff;
  color: #333;
  text-align: center;
  overflow: auto;
  padding: 15px 100px;
  box-shadow: 0 0px 2px 2px #eee;
}
</style>
