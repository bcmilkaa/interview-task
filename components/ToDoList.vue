<template>
		<div>
		<InputBar 
			v-model="newTodoText"
			placeholder="Write your task here"
			@keydown.enter="addTodo"
		/>
		<h2>
		<button
			class="addButton"
			@click="addTodo">Add task
		</button>
		</h2>
		<h1 class="toDoListTitle">Not finished tasks</h1>
		<ul v-if="todos.length" class="toDoList">
			<ListItem
			    class="toDoListElement"
				v-for="todo in todos"
				:key="todo.id"
				:todo="todo"
				@remove="removeToDo(todo.id, todo, listdata)"
			/>
		</ul>
		<ul v-else>
            Nothing to do!
        </ul>
		<DoneList :listTodo="dones" @clicked="addDone"
		/>
	</div>
</template>

<script>
	import InputBar from './InputBar.vue'
	import ListItem from './ListItem.vue'
	import DoneList from './DoneList.vue' 

let nextTodoId = 0

export default {
	components: {
		InputBar, ListItem, DoneList
	},
	props: [
	'listdata'
	],
  data () {
    return {
			newTodoText: '',
      todos: [
				{
					id: nextTodoId,
					text: 'Sell InSign licenses',
					done: false,
					nextTodoId: nextTodoId++
				},
				{
					id: nextTodoId,
					text: 'Practice consulting in front of the mirror',
					done: false,
					nextTodoId: nextTodoId++
				}
			],
	  dones: []
    }
  },
	methods: {
		addTodo () {
			const trimmedText = this.newTodoText.trim()
			if (trimmedText) {
				this.todos.push({
					id: nextTodoId++,
					text: trimmedText,
					done: false
				})
				this.newTodoText = ''
			}
		},

		removeToDo (idToRemove, todo, listdata) {
			this.todos = this.todos.filter(todo => {
				return todo.id !== idToRemove
			})
			this.dones.push(todo)
	},

		addDone(toDotoAdd) {
			this.dones = this.dones.filter(todo => {
				return todo.id !== toDotoAdd.id
			})
			this.todos.push(toDotoAdd)	
		}

	}
}

</script>

<style>
	@import '../src/assets/List.css';
</style>