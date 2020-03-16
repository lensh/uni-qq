<template>
  <!-- 登陆 -->
  <view class="login">
    <view class="top">
      <image src="/static/images/rqk.png" class="img"></image>
      <text>QQ</text>
    </view>
    <view class="form">
      <input type="text" v-model="userinfo.email" class="text" placeholder="邮箱" ref="email" />
      <input type="password" v-model="userinfo.password" class="text" placeholder="密码" />
      <input type="button" :class="{enable:isEnable}" @click="debounce" class="btn" value="登录" />
      
	  <router-link to="/findpass" class="left">忘记密码?</router-link>
      <router-link to="/register" class="right">新用户注册</router-link>
    </view>
  </view>
</template>

<script>
import Util from "@/common/util";
export default {
  name: "login",
  data() {
    return {
      userinfo: {
        email: "", // 邮箱
        password: "" // 密码
      }
    };
  },
  computed: {
    isValidEmail() {
      return Util.checkEmail(this.userinfo.email);
    },
    isValidPwd() {
      return this.userinfo.password != "";
    },
    isEnable() {
      return this.isValidEmail && this.isValidPwd;
    }
  },
  created() {
    this.debounce = Util.debounce(this.login); // 只能放在created里面
  },
  mounted() {
    this.$refs.email.focus();
  },
  methods: {
    async login() {
      if (!this.isValidEmail) {
        this.$message.error("邮箱格式不合法");
        return;
      }
      if (!this.isValidPwd) {
        this.$message.error("密码不能为空");
        return;
      }
      const { email, password } = this.userinfo;
      const { code, message, data } = await this.$http.post("/user/login", {
        email,
        password: Util.encrypt(password) // 密码加密
      });
      if (code == 0) {
		  uni.showToast({
		  	
		  })
        this.$message.success(message);
        Util.setToken(data.token); // 设置token
        this.$store.commit("user/setUserInfo", data.userinfo);
      } else {
        this.$message.error(message);
      }
    }
  }
};
</script>

<style scoped lang="scss" type="text/css">
.login {
  padding: 5rem 2.3rem;
  .top {
    font-size: 1.6rem;
    span {
      margin-left: 0.5rem;
      position: relative;
      bottom: 0.4rem;
      color: #666;
    }
	.img{
		width: 40rpx;
		height: 40rpx;
	}
  }
  .form {
    margin-top: 4rem;
    input {
      font-family: "Microsoft Yahei";
      width: 100%;
      &.btn {
        line-height: 2.3rem;
        background: #ccc;
        color: white;
        margin-top: 3rem;
        &.enable {
          background: #1e90ff;
        }
      }
    }
    a {
      margin-top: 2.4rem;
      color: #1e90ff;
    }
    ::-webkit-input-placeholder,
    ::-moz-placeholder,
    ::-moz-placeholder,
    ::-ms-input-placeholder {
      color: #333;
    }
  }
}
</style>