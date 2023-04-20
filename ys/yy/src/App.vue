<template>
  <div id="app">
    <div class="vote-wrapper">
      <h2>投票</h2>
      <ul>
        <li v-for="(item,index) in list" :key="index">
          <div class="img">
            <img :src="item.avatar" :alt="item.name">
          </div>
          <button>
            <greeting :to="item.name" @click="onClick">like </greeting>
          </button>
        </li>
      </ul>
    </div>
    <p v-for="(item,index) in records" :key="index">
    {{item.time}}-{{item.name}}-{{item.count}}票
    </p>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
export default {
  components: {
    HelloWorld
  },
  data(){
    return{
      list:[
        {avatar:require('./assets/1.jpg'),name:'1'},
        {avatar:require('./assets/2.jpg'),name:'2'},
        {avatar:require('./assets/3.jpg'),name:'3'},
        {avatar:require('./assets/4.jpg'),name:'4'}
      ],
      records:[]
    }
  },
  methods:{
    onClick(name,count){
      console.log(name);
      this.records.push({name,count,time:new Date().toLocaleTimeString()})
    }
  }
}
</script>

<style>
#app{
  font-family: Avenir, Arial, Helvetica, sans-serif;
  text-align: center;
  margin-top: 60px;
}

.vote-wrapper{
  border: 1px solid #999;
  border-radius: 10px;
  width: 600px;
  margin: auto;
}

ul{
  display: flex;
  justify-content: space-around;
  padding: 25px;
  border-top: 1px solid #999;
  margin: 0;
}

li{
  list-style: none;
}

li.img{
  width:110px;
  height: 120px;
  border: 1px solid #999;
  border-radius: 10px;
  border-bottom: 20px;
}

li .img img{
  width: 100%;
  height: 100%;
}
</style>