<template>
  <div>请发表你的评论:
    <br>
    <input type="text" v-model="comments">
    <button @click="comment()">发表</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
      return {
        comments:'',
        kid:sessionStorage.getItem('sid')
      }
    },
    methods:{
      comment(){
        axios({
          method:'post',
          url: 'http://127.0.0.1:8000/homework/comment',
          data: {
            'comments':this.comments,
            'sid':this.kid
          }
        }).then(res=>{
          alert(res.data.msg)
        })
      }
    }
}
</script>

<style>

</style>