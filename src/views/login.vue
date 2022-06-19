<template>
  <div id="background">
    <div id="logo">mysystem</div>
    <div id="login">
      <el-card class="box-card">
        <div id="form">
          <el-input v-model="username" placeholder="请输入内容"></el-input>
          <el-input
            placeholder="请输入密码"
            v-model="password"
            show-password
          ></el-input>
          <el-button type="primary">登录</el-button>
        </div>
      </el-card>
    </div>
    <div id="clock">
      <div id="time">{{ time }}</div>
      <div id="date">{{ date }}</div>
    </div>
    <div id="copyright">copyright © 2022张琴 All Rights Reserved</div>
  </div>
</template>
<style scoped>
#background {
  background-color: darkseagreen;
  position: fixed;
  height: 100%;
  width: 100%;
  top: 0;
  left: 0;
  background-image: linear-gradient(90deg, cyan, purple);
  background-size: 400%;
  animation: myanimation 10s infinite;
}
@keyframes myanimation {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

#logo {
  color: aliceblue;
  font-size: 25px;
  font-weight: 800;
  text-transform: uppercase;
  position: absolute;
  top: 15%;
  left: 15%;
}

#login {
  position: absolute;
  top: 30%;
  left: 38%;
}

.el-card {
  width: 373px;
  height: 210px;
  border-radius: 15px;
  background-color: rgba(255, 255, 255, 0.4);
}

#form {
  line-height: 60px;
  padding-left: 15px;
  padding-right: 15px;
}
#clock {
  color: aliceblue;
  position: absolute;
  top: 70%;
  left: 15%;
  text-align: left;
}
#time {
  font-size: 100px;
}
#date {
  font-size: 35px;
}

#copyright {
  color: aliceblue;
  position: absolute;
  top: 90%;
  left: 38%;
}
</style>
<script>
export default {
  data() {
    return {
      username: "",
      password: "",
      time: "",
      date: "",
    };
  },
  mounted() {
    this.$nextTick(() => {
      setInterval(this.update_clock, 1000);
    });
  },
  methods: {
    update_clock: function (e) {
      var d = new Date();
      var year = d.getFullYear();
      if (year < 10) {
        year = "0" + year;
      }
      var month = d.getMonth();
      if (month < 10) {
        month = "0" + month;
      }
      var day = d.getDate();
      if (day < 10) {
        day = "0" + day;
      }
      var hour = d.getHours();
      if (hour < 10) {
        hour = "0" + hour;
      }
      var minute = d.getMinutes();
      if (minute < 10) {
        minute = "0" + minute;
      }
      this.time = hour + ":" + minute;
      this.date = year + "/" + month + "/" + day;
    },
  },
};
</script>
