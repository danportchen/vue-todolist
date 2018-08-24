<template>
  <div class="view">
    <h1 class="title">{{msg}}</h1>
    <input v-model= "newStr" @keyup.enter= "addData"/>
    <ul>
      <li v-for = "item in items" :key= "item.id" v-bind:class = "{finish:item.isFinished}" @click = "toggleFinish(item)">
        {{item.text}}
      </li>
    </ul>
  </div>
  
</template>
<script>
//new view
  export default {
    name: 'List',
    // data: function(){
    //   return{}
    // }
    data() {
      return {
        title: 'Todo列表', //title
        id: 0,
        items: [           // todo list
          {
            text: '今天晚上跑步',
            isFinished: true
          },
          {
            text: '今天早餐吃麵包',
            isFinished: false
          },
        ],
        newStr: '',
        }
      },
    props: {
      msg: {
        type: String,
        default: '我是誰？',
      }
    },
    methods: {
      toggleFinish: function(item){
        item.isFinished = !item.isFinished;
      },
      addData: function(){
        // 
        this.items.push({
          text: this.newStr,
          isFinished: false
        },);
        this.$emit('myMsg', this.newStr);
        this.newStr = '';
      },
    },
  }
</script>

<style>
  .view {
    width: 400px;
    border: 2px solid gray;
    margin: 20px auto;
    background: #12c2e9;  /* fallback for old browsers */
    
  }

  .view .title {
    border-bottom: 1px solid gray;
  }
  .view ul li {
    margin: 10px 0;
    list-style: none;
  }
  .view .finish {
    color: gray;
    text-decoration: line-through;
  }
</style>
