<template>
    <div>
        <h1 class="doneListTitle">Finished tasks</h1>
        <ul v-if="listTodo.length" class="doneList">
            <ListItem 
                      class="doneListElement"
                      v-for="todo in listTodo"
                      :key="todo.id"
                      :todo="todo"
                      @remove="isNotDone(todo.id, todo)" />
        </ul>
        <ul v-else>
            Nothing done so far, don't be lazzy!
        </ul>
    </div>
</template>

<script>
import ListItem from './ListItem.vue';
import ToDoList from './ToDoList.vue';


export default {
	components: {
        ListItem, ToDoList
        },
        props: [
            'listTodo'
        ],

        methods: {

        isNotDone(idToRemove, todo) {
            this.$emit('clicked', todo, todo.id)
        }

	}
}

</script>

<style>
    @import '../src/assets/List.css';
</style>
