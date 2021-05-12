<template>
    <li>
        <input class="checkBox" type="checkbox" v-model="todo.done" disabled />
        {{ todo.text }}
        <button @click="$emit('remove', this)" class="removeButton">
            // Unicode to display the X
            &#10006;
        </button>
    </li>
</template>

<script>
    export default {
        props: {
            todo: {
                type: Object
            }
        }
    }
</script>

<style>
    @import '../src/assets/Button.css';
</style>