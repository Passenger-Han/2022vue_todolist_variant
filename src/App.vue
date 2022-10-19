<template>
  <Head @submitTodo="submit"></Head>
  <List :todoListData="todoList" @removeTodo="remove"></List>
  <Foot @removeAllTodo="removeAll"></Foot>
</template>

<script>
import Head from './components/Head.vue';
import List from './components/List.vue';
import Foot from './components/Foot.vue';

export default {
  components: {
    Head,
    List,
    Foot,
  },

  data(){
    return {
      todoList: [],
    }
  },

  created(){
    for (let i = 0; i < localStorage.length; i++){
      this.todoList.push(localStorage.key(i));
    }
  },

  methods: {
    submit: function(inputvalue){
      this.todoList.push(inputvalue);
      localStorage.setItem(inputvalue, inputvalue);
    },

    remove: function(element, index){
      this.todoList.splice(index, 1);
      localStorage.removeItem(element);
    },

    modify: function(origElement, index, newElement){
      this.todoList.splice(index, 1, newElement);
      localStorage.removeItem(origElement);
      localStorage.setItem(newElement, newElement);
    },

    removeAll: function(){
      this.todoList = [];
      localStorage.clear();
    },
  }
}
</script>

<style>
@import url(./assets/initial.css);

#app {max-width: 376px; margin: 0 auto; padding: 16px;}
</style>