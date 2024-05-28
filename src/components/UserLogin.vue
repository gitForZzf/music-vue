<template>
    <div class="login-page">
      <h2>登录</h2>
      <div class="login-form">
        <div v-if="!isWeChatLogin">
          <input type="text" placeholder="用户名" v-model="username" required />
          <input type="password" placeholder="密码" v-model="password" required />
          <button @click="loginWithCredentials">登录</button>
        </div>
        <div v-if="isWeChatLogin" class="wechat-login">
          <p>微信扫码登录</p>
          <!-- 这里放置微信扫码登录的二维码 -->
          <img src="../assets/WeiXinQRcode.png" alt="微信扫码登录" />
          <button @click="loginWithWeChat">确认登录</button>
        </div>
        <button @click="switchLoginMethod">切换登录方式</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        username: '',
        password: '',
        isWeChatLogin: false // 控制登录方式的切换，false为用户密码登录，true为微信扫码登录
      };
    },
    methods: {
      loginWithCredentials() {
        // 这里可以编写用户密码登录的逻辑，比如发送登录请求到后端进行验证
        console.log('用户密码登录', this.username, this.password);
      },
      loginWithWeChat() {
        // 这里可以编写微信扫码登录的逻辑，比如通过扫码结果进行验证
        console.log('微信扫码登录');
      },
      switchLoginMethod() {
        // 切换登录方式
        this.isWeChatLogin = !this.isWeChatLogin;
      }
    }
  };
  </script>
  
  <style scoped>
  .login-page {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }
  
  .login-form {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  
  .login-form input {
    margin-bottom: 10px;
    padding: 5px;
    width: 200px;
  }
  
  .login-form button {
    margin-top: 10px;
    padding: 5px 10px;
  }
  
  .wechat-login {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 20px;
  }
  
  .wechat-login img {
    width: 200px;
    height: 200px;
    margin-bottom: 10px;
  }
  </style>