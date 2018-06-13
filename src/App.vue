<template>
  <div id="app">
    <button @click="isPay=true">点击支付</button>
    <vue-pay-keyboard ref="pay" :isPay='isPay' @pasEnd='pasEnd' @close='isPay=false'></vue-pay-keyboard>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      isPay: false
    }
  },
  methods: {
    pasEnd(val) {
      console.log(val) //得到密码 可能会进行一些加密动作
      setTimeout(() => {
        // 模拟请求接口验证密码中 ..
        if (val === '111111') {
          this.$refs.pay.$payStatus(true) // 传递给子组件
        } else {
          this.$refs.pay.$payStatus(false)
        }
      }, 1000)
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
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
