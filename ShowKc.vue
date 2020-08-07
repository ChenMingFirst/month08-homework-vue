<template>
    <div>
        <p>{{ message }}</p>
        <table>
            <tr>
                <td>课程名称</td>
                <td>操作</td>
                <td>评论</td>
            </tr>
            <tr v-for="i in list" :key="i.id">
                <td>{{ i.name }}</td>
                <td><button @click="like(i.id)">关注</button> 
                <button @click="comment(i.id)">评论</button> </td>
                <td></td>
            </tr>
        </table>
    </div>
</template>


<script>
import axios from 'axios'
export default {
    data() {
        return {
            list : [],
            name : sessionStorage.getItem('name'),
            message:'',
            comment_list : ''
        }
    },
    mounted() {
        axios({
            method:'get',
            url: 'http://127.0.0.1:8000/homework/showkc',
        }).then(res=>{
            this.list = res.data.list
            this.comment_list = res.data.comment
        })
    },
    methods:{
        like(id){
            console.log(id)
            console.log(this.name)
            axios({
                method:'post',
                url: 'http://127.0.0.1:8000/homework/showkc',
                data: {
                    'username':this.name,
                    'kid':id
                }
            }).then(response => {
                if (response.data.code == 200) {
                    console.log(response.data);
                } else {
                    console.log(response.data);
                }
            })
        },
        comment(id){
            sessionStorage.setItem('sid',id)
            this.$router.push({'name':'comment'})
        }
    }
}
</script>