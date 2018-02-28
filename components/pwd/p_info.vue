<template>
  <div id="bigbox">
      <ul>
          <li>
              <span class="name">用户名</span>
              <div class="box">
                  <span class="info">{{username}}</span>
                  <img src="../../image/c_right.jpg">
              </div>
          </li>
          <li @click="changephone">
              <span class="name">手机号码</span>
              <div class="box">
                  <span class="info">{{phone}}</span>
                  <img src="../../image/c_right.jpg">
              </div>
          </li>
          <li>
              <span class="name">性别</span>
              <div class="box">
                  <span class="info">{{sex}}</span>
              </div>
          </li>
          <li>
              <span class="name">生日</span>
              <div class="box">
                  <span class="info">{{birth}}</span>
              </div>
          </li>
          <li  @click="changepwd">
              <span class="name">密码设置</span>
              <div class="box">
                  <img src="../../image/c_right.jpg">
              </div>
          </li>
      </ul>
      <div id="btn" @click="logout">退出登录</div>
  </div>
</template>
<script>
   var url = location.href;
   var arr = url.split("#");
    var $ = require('jquery')
    export default{
        data:function(){
            return {
                id:this.$store.state.loginid,
                username:'',
                phone:'',
                sex:'',
                birth:''
            }
        },
        methods:{
            getInfo:function(){
                var that = this;
                $.ajax({
                    type:'post',
                    url:'http://118.24.4.133:8888/user/getInfoById',
                    data:{
                        id:this.$store.state.loginid
                    },
                    success:function(data){
                        console.log(data)
                        that.username = data[0].name;
                        that.phone = data[0].phone;
                        that.sex =  data[0].sex ;
                        that.birth = data[0].birth ; 
                    }
                })
            },
            changephone:function(){
              window.location.href=arr[0]+"#/change"
            },
            changepwd:function(){
              window.location.href=arr[0]+"#/pwdmain"
            },
            logout:function(){
              window.location.href=arr[0]+"#/index/home"
            }
        },
        mounted:function(){
            this.getInfo();
        }
    }
</script>
<style scoped>
#btn{
    font-size: 0.24rem;
    color: #8a8a8a;
    background: #ffffff;
    height: 0.9rem;
    line-height: 0.9rem;
    text-align: center;
    margin-top: 0.2rem;
}
#bigbox{
    margin-top: 0.2rem;
    background: #ffffff;
}
li{
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 1px solid #f2f2f2;
    margin-left: 0.25rem;
    height: 0.9rem;
    padding-right: 0.25rem;
}
.name{
    color:#191919;
    font-size: 0.27rem;
    margin-left: 0.05rem;
}
.box{
    display: flex;
    justify-content: flex-end;
    align-items: center;
}
.info{
    color:#8a8a8a;
    font-size: 0.24rem;
}
img{
    width: 0.18rem;
    height: 0.28rem;
    margin-left: 0.2rem;
}
</style>
