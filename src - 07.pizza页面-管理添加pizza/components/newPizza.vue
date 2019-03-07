<template>
  <div class="newpizza">
     <h3 class="text-center text-warning">添加新Pizza</h3>
     <form>
        <div class="form-group">
            <label for="input1">品种：</label>
            <input type="text" v-model="newPizza.name" class="form-control" id="input1"  placeholder="给这个pizza起个名字吧...">
        </div>
        <div class="form-group">
            <label class="label" for="input2">商品描述:</label>
            <textarea id="input2" v-model="newPizza.description" placeholder="请输入商品的相关描述..." cols="85" rows="2"></textarea>
        </div>
        <h3>尺寸&价格</h3>
        <div class="form-group float">
            <span class="span"> 尺寸：</span>   
            <select class="form-control" v-model="newPizza.size1" id="input3">
            <option>5</option>
            <option>7</option>
            <option>9</option>
            <option>11</option>
            <option>14</option>
            </select>
        </div>
        <div class="form-group float">
            <label for="input4">价格：</label>
            <input type="text" v-model="newPizza.price1" class="form-control" id="input4">
        </div>
        <div class="form-group float">
            <span class="span"> 尺寸：</span>   
            <select class="form-control" v-model="newPizza.size2" id="input5">
            <option>7</option>
            <option>5</option>
            <option>9</option>
            <option>11</option>
            <option>14</option>
            </select>
        </div>
        <div class="form-group float">
            <label for="input6">价格：</label>
            <input type="text"  v-model="newPizza.price2"  class="form-control" id="input6">
        </div>
        <button class="btn btn-primary btn-block" @click.prevent="addPizza">添加pizza</button>
    </form> 
  </div>  
</template>
<script>
import axios from 'axios'
export default {
   data(){
      return{
        newPizza:{}   
      } 
   },
   methods:{
     addPizza(){
       var data ={
          name:this.newPizza.name,
          description:this.newPizza.description,
          options:[
            {
              size:this.newPizza.size1,
              price:this.newPizza.price1
            },
            {
              size:this.newPizza.size2,
              price:this.newPizza.price2
            },
          ]
        }
       axios.post('./menu-jsx.json',data)
       .then(res=>{
          console.log(res.data) 
       })
     }
   } 
}
</script>
<style scoped>
.label{display: block;}
#input3,#input5{width: 65px;}
/* #input3,#input4,#input5,#input6{
    display: inline;
}
.float{float: left;} */
</style>
