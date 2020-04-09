<template>
  <div id="app">
    <div class = "logo">
      <img src="./assets/logo.png">
    </div>
    <section class="todoapp">
      <Header @insertTodo="insertTodo" />
      <Todo :todos= "todos" @removeTodo = "removeTodo" @toggleDone = "toggleDone" @updateTodo = "updateTodo" />
      <Footer />
    </section>
  </div>
</template>

<script>
import './assets/css/main.css'
import Header from './components/todoHeader'
import Todo from './components/todoApp'
import Footer from './components/todoFooter'

let id = 0

export default {
  name: 'App',
  components: {
    Header,
    Todo,
    Footer
  },
  data () {
    return {
      todos: [
        {
          id: id++,
          text: '영화보기',
          isDone: true
        },
        {
          id: id++,
          text: 'js공부하기',
          isDone: false
        },
        {
          id: id++,
          text: 'ts공부하기',
          isDone: false
        }
      ]
    }
  },
  methods: {
    insertTodo (text) {
      this.todos = [
        ...this.todos,
        {
          id: id++,
          text,
          isDone: false
        }
      ]
    },
    removeTodo (id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    },
    toggleDone (id) {
      const todos = [...this.todos]
      const todo = todos.find(todo => todo.id === id)

      if (todo) {
        todo.isDone = !todo.isDone
        this.todos = todos
      }
    },
    updateTodo ({id, text}) {
      const todos = [...this.todos]
      const todo = todos.find(todo => todo.id === id)

      if (todo) {
        todo.text = text
        this.todo = todos
      }
    }
  }
}
</script>

<style>
.logo{ text-align: center;}
</style>
