<template>
  <div class="register container text-center mt-5">
    
    <img src="../../static/logo.png" width="100" alt="">
    <h3>注册</h3>
    <form>
  <div class="form-group">
    <input type="email" class="form-control" id="input1" v-model="username"  placeholder="请输入您的邮箱">
  </div>
  <div class="form-group">
    <input type="password" class="form-control" id="input2" v-model="password" placeholder="请输入您的密码">
  </div>
  <div class="form-group">
    <input type="password" class="form-control" id="input3" v-model="repassword" placeholder="请再次确认您的密码">
  </div>
  <div class="form-check">
    <input type="checkbox" class="form-check-input" id="exampleCheck1">
    <label class="form-check-label" for="exampleCheck1">Remeber me </label>
  </div>
  <button type="submit" @click.prevent="onSubmit" class="btn btn-primary btn-block">Sign Up</button>
</form>
  </div>
</template>

<script>
// axios引入
import axios from 'axios';
export default {
  name: 'Register',
  data () {
    return {
      username:'',
      password:'',
      repassword:''
    }
  },
  methods:{
    onSubmit(){
      // 非空验证
      if(this.password==''&&this.username==''){
        return
      }
      //进行当前密码的重复确认
      if(this.password===this.repassword){
        var formData={
          username:this.username,
          password:this.password
        }
        axios.post('./user-jsx.json',formData)
          .then(res=>{
            console.log('当前数据抛出成功')
            console.log(res.data)
            // 当注册成功时跳转到登录页，引导用户登陆
            // 两种方法实现跳转
            // 堆栈法
            // this.$router.push('/login')
            // 替代法
            this.$router.replace('/login')
          })
      } 
    }
  }
 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .form-control{
    width: 500px;
  }
  .register{
    width: 500px;
    margin:0 auto;
  }
  .btn-block{
    width: 107%; 
  }
</style>
