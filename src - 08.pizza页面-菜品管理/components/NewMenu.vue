<template>
    <div class="newmenu">
       <h3 class="text-center text-warning">菜单管理</h3>
       <table class="table text-center">
        <thead>
          <tr>
            <th scope="col">序号</th>
            <th scope="col">品种</th>
            <th scope="col">删除</th>
          </tr>
        </thead>
        <tbody v-for="(item,index) in items" :key="index">
           <tr>
            <td>{{index+1}}</td>
            <td>{{item.name}}</td>
            <td><button class="btn btn-danger" @click="delItem(item)">Delete</button></td>
          </tr>
        </tbody>
        </table>
    </div>
</template>
<script>
import axios from 'axios'
export default {
  data(){
    return{
    //   items:[{name:'111'},{name:'222'},{name:'333'}]
    //  items:[{name:'111',id:'-L_GhzljtAVxpPho'}]
    items:[]
    }  
  },
  mounted(){
      var that = this  
        axios.get('./menu-jsx.json')
        .then(res=>{
        console.log(res.data)
        //   在这里我需要获取下key值==》存储为id，方便通过id删除当前项
        for(var key in res.data){
            console.log(key)
            var item = res.data[key]
            item.id=key
            that.items.push(item)
        }
        console.log(that.items)  
        })
  },
  methods:{
    delItem(item){
      axios.delete('./menu-jsx/'+item.id+'.json')
      .then(res=>{
         console.log('删除成功')
         this.$router.push('/menu') 
        //记住刷新页面的方法
        // location.reload()  
      })  
    },
  }  
}
</script>
<style>

</style>
