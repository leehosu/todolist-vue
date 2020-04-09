<template>
  <header class="header">
    <h1>Vue TodoList</h1>
    <input
      class="new-todo"
      v-model="text"
      autofocus
      autocomplete="off"
      placeholder="Please insert about todos,,"
      @keypress="handleTodo"
    />
  </header>
</template>

<script>
export default {
  data () {
    return {
      text: ''
    }
  },
  methods: {
    handleTodo ({ keyCode }) {
      const { text } = this

      if (keyCode === 13 && text !== '') {
        this.$emit('insertTodo', text)
        this.text = ''
      }
    }
  }
}
</script>
<style>
h1 {
  position: absolute;
  top: -155px;
  width: 100%;
  font-size: 80px;
  font-weight: 100;
  text-align: center;
  color: black;
  -webkit-text-rendering: optimizeLegibility;
  -moz-text-rendering: optimizeLegibility;
  text-rendering: optimizeLegibility;
}
</style>
