<template>
    <div>
        <h1 class="doneListTitle">Finished tasks</h1>
        <ul v-if="dones.length" class="doneList">
            <ListItem 
                      class="doneListElement"
                      v-for="todo in dones"
                      :key="todo.id"
                      :todo="todo"
                      @remove="NotDone(todo.id, todo)" />
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
            'dones'
        ],

        methods: {

        NotDone(idToRemove, todo) {
            this.$emit('clicked', todo, todo.id)
        }

	}
}

</script>

<style>
    @import '../src/assets/List.css';
</style>
