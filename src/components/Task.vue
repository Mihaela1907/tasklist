<template>
        <div>
        <span class="title"
            contenteditable="true"
            v-on:keydown.enter="updateTask($event, list)"
            v-on:blur="updateTask($event, list)"
            v-bind:class="{completed: list.isComplete}">{{list.title}}</span> 
        <input type="checkbox" v-on:change="completeTask(list)" v-bind:checked="list.isComplete"/>
        <span class="remove" v-on:click="removeTask(index)">x</span>        
        </div>
</template>


<script>
export default {
    name: 'Task',
    props: {
        list: Object
    }
}
</script>


<style lang="scss" scoped>

</style>