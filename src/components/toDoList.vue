<template>
  <div class="container">
    <div class="row">
      <div class="col-md-6 offset-md-3 t-center">
        <h1>To Do App</h1>
          <div class="formSide">
            <label>New To Do</label>
            <input id="itemForm" type="text" v-model="taskData">
            <button @click="getData" class="btn btnColor" >Add To Do</button>
          </div>
        <h4>To Do List</h4>
        <hr>
        <ul>
          <transition-group name="fade" tag="ul">
            <li v-for="(item, index) in array" :key="item.id"><span>{{ item }}</span><button class="btn" @click="removeData(index)">Remove</button></li>
          </transition-group>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    data(){
      return {
        taskData : undefined,
        array : [],
      }
    },
    methods : {
      getData(){
        this.array.push(this.taskData);
        this.taskData = undefined;
      },
      removeData(index){
        this.array.splice(index,1);
      }
      
    },
}
</script>

<style>

body{
  background-color: #27292D;
  font-family: Arial, Helvetica, sans-serif;
  color: #fff;
}

.formSide{
  display: flex;
  flex-direction: column;
}

h1{
  text-align: center;
  margin-top: 50px;
  color: #fff;
}

label{
  color: #fff;
  margin-bottom: 5px;
}

.btnColor{
  background-color: #FFC137;
  margin-bottom: 20px;
}

input{
  margin-bottom: 10px;
  border-radius: 10px;
  height: 50px;
  background-color: #27292D;
  border: 1px solid #727476;
}

.btn{
  border-radius: 10px;
  border: 1px solid #727476;
}

ul{
  padding-left: 0pt;
}

li{
  border: 1px solid #727476;
  border-radius: 10px;
  padding: 15px;
  margin-bottom: 10px;
  justify-content: space-between;
  list-style: none;
}

li .btn{
  float: right!important;
  background-color: #FFC137!important;
  width: 80px;
  height: 35px;
  margin-top: -5px;
  
}

li .btn:hover{
  background-color: lightpink!important;
}

  .fade-enter {
    opacity: 0;
  }
  .fade-enter-active{
    transition: opacity 1s;
  }
  .fade-leave {
    opacity: 0;
  }
  .fade-leave-active{
    transition: opacity 1s;
    opacity: 0;
  }
</style>
