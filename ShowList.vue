<template>
    <div>
        <table>
            <tr>
                <td>课程名称</td>
                <td>内容</td>
            </tr>
            <tr v-for="i in list" :key="i">
                <td>{{ i.name }}</td>
                <td>关注</td>
            </tr>
        </table>
    </div>
</template>


<script>
import axios from 'axios'
export default {
    data() {
        return {
            list : []
        }
    },
    mounted() {
        axios({
            method:'get',
            url: 'http://127.0.0.1:8000/showkc/',
        }).then(res=>{
            this.list = res.data.list
        })
    },
}
</script>