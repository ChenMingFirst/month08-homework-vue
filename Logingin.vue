<template>
  <div>
      输入账号查看：<input type="text" v-model="name">
      <button @click="login">进入</button>
  </div>
</template>

<script>
export default {
    data() {
        return {
            name :''
        }
    },
    methods:{
        login(){
            sessionStorage.setItem('name',this.name)
            this.$router.push({'name':'ShowKc'})
        }
    }
}
</script>
