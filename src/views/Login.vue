<template>
  <div>
    <form action="" v-if="!isReg">
      <div>用户名：</div>
      <input type="text" v-model="name">
      <div>密码：</div>
      <input type="password" v-model="password">
      <div><button type="button" @click="login()">登录</button>
        <button type="button" @click="reg()">注册</button></div>

    </form>
    <form v-else>
      <div>用户名：</div>
      <input type="text" v-model="name">
      <div>密码：</div>
      <input type="password" v-model="password">
      <div>再次输入密码：</div>
      <input type="password" v-model="repeat">
      <div>
        <button type="button" @click="addUser()">确定</button>
        <button type="button" @click="cancel()">取消</button>
      </div>

    </form>
  </div>

</template>
<script>

    export default {
      name:"Login",
      data(){
          return{
              isReg:false,
            name:'',
            password:'',
            repeat:''
          }
      },
      methods: {
          login(){
              if(localStorage.getItem("name")===this.name&&localStorage.getItem("password")===this.password){
                  this.name=''
                  this.password=''
                this.$router.push('/home/list')
              }else{
                this.password=''
                  alert("用户名或密码错误！")
              }


          },
          reg(){
              this.isReg=true
          },
          cancel(){
              this.isReg=false
          },
          addUser(){
              if(this.password===this.repeat){
                localStorage.setItem("name",this.name)
                localStorage.setItem("password",this.password)
                this.name=''
                this.password=''
                this.repeat=''
                this.isReg=false


              }else{
                  alert("两次输入密码不一致！")
              }
          }
      }
    }
</script>
<style scoped>

</style>
