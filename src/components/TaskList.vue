<template>
  
<div id="todoApp">

  <form name="todo-form" method="post" action="" v-on:submit.prevent="addTask">
    <input name="add-todo" type="text" v-model="addTodoInput" v-bind:class="{error: hasError}"/>
    <button type="submit">Add task</button>
  </form>
  
  <div class="todo-lists" v-if="lists.length">
    <ul>
      <li v-for="(list,index) in lists" :key="index">
        <span class="title"
            contenteditable="true"
            v-on:keydown.enter="updateTask($event, list)"
            v-on:blur="updateTask($event, list)"
            v-bind:class="{completed: list.isComplete}">{{list.title}}</span> 
        <input type="checkbox" v-on:change="completeTask(list)" v-bind:checked="list.isComplete"/>
        <span class="remove" v-on:click="removeTask(index)">x</span>
      </li>
    </ul>
  </div>
  
</div>

</template>

<script>
//import Task from './Task.vue'

export default {
  data () {
    return {
        addTodoInput: '',
        lists: [],
        hasError: false
    }
  },
  //components: {
  //   Task
  //},
  methods: {
      addTask() {
        if(!this.addTodoInput){ 
          this.hasError = true;
          return;               
        }

        this.hasError = false;

        this.lists.push({
          id:this.lists.length+1,
          title: this.addTodoInput,
          isComplete: false
        });

        this.addTodoInput = '';
      },

      updateTask(e, list) {
        e.preventDefault();
        list.title = e.target.innerText;
        e.target.blur();
      },

      completeTask(list){
        list.isComplete = !list.isComplete;
      },

      removeTask(index){
        this.lists.splice(index, 1);
      }
  }
}
</script>

<style lang="scss" scoped>
  :root{font-family: Arial;}
input[type=text]{
  font-size:16px;
  padding: 8px;
  border-radius: 10px;
  border: 1px solid #c4c4c4;
}

button{
  background: #3498db;
  background-image: linear-gradient(to bottom, #3498db, #2980b9);
  border-radius: 28px;
  
  color: #ffffff;
  font-size: 16px;
  padding: 8px 20px;
  border: none;
  cursor:pointer;
}
button:hover {
  background: #3cb0fd;
  background-image: linear-gradient(to bottom, #3cb0fd, #3498db);
}
input[type=text].error{border: 1px solid red;}
[contenteditable=true]:focus{
  
  
  overflow: hidden;
  border: 1px solid transparent;

  -webkit-appearance: textfield;
  -moz-appearance: textfield;
  appearance: textfield;

  white-space: nowrap;
  border-radius: 10px; 
}

.title{
  display: inline-block;
  width: 200px;
  border: 1px solid transparent;
  padding: 8px;
  font-size: 16px;
  vertical-align:middle;
}

.title:hover{
  border:1px solid #c4c4c4;
  border-radius: 10px;
}

.remove{
  cursor:pointer;
  display:inline-block;
  border: 1px solid #c4c4c4;
  border-radius: 50%;
  padding:0px 4px;
}
.remove:hover{
  background: #3cb0fd;
}

.completed{
  text-decoration: line-through;
}
</style>
