<template>
  <div>
    <span
      class="title"
      contenteditable="true"
      v-bind:class="{completed: task.isComplete}">{{task.title}}</span>
    <input type="checkbox" @change="completeTask(task)" v-bind:checked="task.isComplete" />
    <span class="remove" @click="removeTask(task)">
        <img class="trashImg" src="https://cdn4.iconfinder.com/data/icons/primitive/512/trash_can-512.png"/>
    </span>
  </div>
</template>


<script>
export default {
  name: "Task",
  props: {
    task: Object
  },
  methods: {
    completeTask(task) {
      this.$emit("complete-task", task);
    },
    removeTask(task) {
      this.$emit("remove-task", task);
    }
  }
};
</script>


<style lang="scss" scoped>

[contenteditable="true"] {
	&:focus {
		overflow: hidden;
		border: 1px solid transparent;
		white-space: nowrap;
		border-radius: 10px;
	}
}

.title {
	display: inline-block;
	padding-top: 6px;
	padding-bottom: 7px;
	padding-left: 7px;
	font-size: 16px;
	vertical-align: middle;
	cursor: pointer;
	width: 83%;
	text-align: left;
	background-color: rgba(black, .05);
	border: 1px solid rgba(black, .1);
	&:hover {
		border: 1px solid #c4c4c4;
		border-radius: 10px;
	}
}

.remove {
	cursor: pointer;
	height: 25px;
	width: 25px;
	display: inline-block;
	padding-top: 4px;
	&:hover {
		background: #3cb0fd;
	}
}

.trashImg {
    height: 20px;
    width: 20px;
}
.completed {
  text-decoration: line-through;
}
</style>