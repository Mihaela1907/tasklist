<template>
    <div>
        <form name="todo-form" method="post" action v-on:submit.prevent="addTask">
            <input name="add-todo" type="text" v-model="addTodoInput" v-bind:class="{error: hasError}" />
            <button type="submit">Add</button>
        </form>
    </div>
</template>


<script>

</script>


<style lang="scss" scoped>

</style>
