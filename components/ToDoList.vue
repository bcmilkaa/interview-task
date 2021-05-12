<template>
	<div>
		<InputBar
			class="inputBarToDoList"
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
		<h2 class="toDoListTitle">Not finished tasks</h2>
		<ul v-if="todos.length" class="toDoList">
			<ListItem
			    class="toDoListElement"
				v-for="todo in todos"
				:key="todo.id"
				:todo="todo"
				@remove="removeToDo(todo.id, todo, listdata)"
			/>
		</ul>
		<ul v-else class="toDoListTitle">
        Nothing to do!
        </ul>
		
		<DoneList :dones="dones" @clicked="addDone"
		/>
	</div>
</template>

<script>
	import InputBar from './InputBar.vue'
	import ListItem from './ListItem.vue'
	import DoneList from './DoneList.vue' 

// Initialises the toDo id
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
		
		// Adds the input at the inputbar to the toDo-List and clears the inputbar.
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
		
		// Removes the toDo with the ID = idToRemove and adds it to the dones list.
		removeToDo (idToRemove, todo) {
			this.todos = this.todos.filter(todo => {
				return todo.id !== idToRemove
			})
			todo.done = true
			this.dones.push(todo)
		},
		
		// Removes the done toDo from the done list and adds it to the toDo-List.
		addDone(toDotoAdd) {
			this.dones = this.dones.filter(todo => {
				return todo.id !== toDotoAdd.id
			})
			toDotoAdd.done = false
			this.todos.push(toDotoAdd)	
		}

	}
}
</script>

<style>
	@import '../src/assets/List.css';
</style>