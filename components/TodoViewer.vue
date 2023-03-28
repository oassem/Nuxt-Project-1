<template>
    <div>
        <slot name="main"></slot>
        <h1>{{ title }}</h1>
        <button @click="fetchTodoList">Fetch data</button>
        <!--  <pre>
        {{ todoList }}
      </pre> -->
        <ul>
            <li v-for="todo in todoList" :key="todo.id">
                <input type="checkbox" :checked="todo.completed"> {{ todo.title }}
            </li>
        </ul>
    </div>
</template>
  
<script>
export default defineNuxtComponent({
    data() {
        return {
            todoList: [],
        };
    },
    props: ['title', ''],
    methods: {
        async fetchTodoList() {
            await fetch('https://jsonplaceholder.typicode.com/todos')
                .then(response => response.json())
                .then(json => { this.todoList = json });
        }
    }
})
</script>