<template lang="pug">
.to-do(:class="computedClass")
  .todo-inner
    .heading {{ title }}
    .todo-container
      input#input.todo-input(
        autofocus
        placeholder="what should I do?"
        @keyup.enter="addTodo"
        v-model="newTodo"
      )
      button.add-btn(@click="addTodo") Add
  .to-do-reminder(v-if="todos.length === 0")
    p.reminder Start day with a new todo!
  .todos-container
    ul.todo-list
      li.todo-item(v-for="todo in todos")
        span {{ todo }}
        button.close-btn(@click="removeTodo")
  .todo-footer(v-if="todos.length > 0")
    .todo-info {{ totalToDos }}
</template>

<script lang="ts">
  export default {
    data() {
      return {
        todos: Array(),
        newTodo: null || '',
        title: 'My To Do',
      };
    },

    mounted() {
      const loadedTodos = localStorage.getItem('todos') || '';
      this.todos = loadedTodos ? JSON.parse(loadedTodos) : [];
    },

    methods: {
      addTodo() {
        if (!this.newTodo) {
          return;
        }

        this.todos.push(this.newTodo);
        this.newTodo = '';
      },

      removeTodo(todo: string) {
        this.todos.splice(this.todos.indexOf(todo), 1);
      },

      saveTodo() {
        let parsed = JSON.stringify(this.todos);
        localStorage.setItem('todos', parsed);
      },
    },

    computed: {
      totalToDos() {
        return this.todos.length + ' ' + 'left';
      },
    },

    watch: {
      todos: {
        handler(newValue: any, oldValue: any) {
          this.saveTodo();
        },
        deep: true,
      },
    },
  };
</script>

<style style scoped lang="scss">
  .to-do {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    gap: 5px;

    & .todo-inner {
      display: flex;
      gap: 20px;
      width: 100%;
      background-color: #f0f3f5;
      border-top-right-radius: 40px;
      border-top-left-radius: 40px;
      padding: 20px;
      display: flex;
      flex-direction: column;
      gap: 30px;

      & .todo-container {
        display: flex;
        gap: 15px;

        & input.todo-input {
          width: 100%;
          height: 40px;
          padding: 4px;
          border-radius: 50px;
          border: none;
          padding: 5px 20px;
          box-shadow: inset 0px 1px 3px rgba(28, 33, 34, 0.25);

          &:focus {
            box-shadow: 0 0 2px 2px #6750a4;
            outline: 0;
          }
        }

        & .add-btn {
          width: 100px;
          height: 40px;
          color: white;
          background: #6750a4;
          position: relative;
          border: none;
          transition: all 0.3s ease;
          border-radius: 100px;
          cursor: pointer;
          font-weight: 600;
          display: flex;
          justify-content: center;
          align-items: center;
          padding: 10px 24px;
          gap: 8px;
          font-style: normal;
          font-size: 14px;
          line-height: 20px;

          &:hover {
            background-color: #6750a4;
            box-shadow: 0px 1px 2px rgba(0, 0, 0, 0.3), 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
          }

          &:focus {
            color: rgba(255, 255, 255, 0.8);
            background-color: #6750a4;
          }
        }
      }

      & .heading {
        color: #5c5c5c;
        align-self: center;
        font-size: 40px;
      }
    }

    & .todo-list {
      border-bottom-right-radius: 8px;
      border-bottom-left-radius: 8px;
      display: flex;
      flex-direction: column;
      gap: 5px;

      & .todo-item {
        color: #1c2122;
        background-color: #f0f3f5;
        transition: background-color 0.3s ease;
        position: relative;
        padding: 5px 20px;

        &:hover {
          background-color: #bebebe;

          & button.close-btn {
            opacity: 1;

            &::before,
            &::after {
              background-color: #6750a4;
            }
          }
        }

        & button.close-btn {
          height: 100%;
          background-color: transparent;
          position: absolute;
          border: none;
          opacity: 0.3;
          transition: all 0.3s ease;
          right: 20px;
          bottom: 10px;
          z-index: 100;

          &::before,
          &::after {
            content: '';
            position: absolute;
            width: 2px;
            height: 20px;
            background-color: #1c2122;
          }

          &::before {
            transform: rotate(-45deg);
          }

          &::after {
            transform: rotate(45deg);
          }
        }
      }
    }

    & .todo-footer {
      padding: 20px;
      background-color: #f0f3f5;
      border-bottom-right-radius: 20px;
      border-bottom-left-radius: 20px;
      display: flex;
      gap: 30px;

      & .todo-info {
        color: #1c2122;
      }
    }
  }
</style>
