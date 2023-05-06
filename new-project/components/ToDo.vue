<template lang="pug">
.to-do
    .todo-inner
        h2.heading My to do
        .todo-container
            input.todo-input(
                autofocus
                id="input"
                v-model="newTodo"
                placeholder="what should I do?"
                @keyup.enter="addTodo"
            )
            button.add-btn(@click="addTodo")
    .todos-container
        ul.todo-list
            li.todo-item(
                v-for="todo in todos"
            )
                span {{ todo }}
                button.close-btn(@click="removeTodo")
    .todo-footer(v-if="todos.length > 0")
        .todo-info {{ totalToDos }}
</template>

<script>
export default {
    setup() {},

    data: () => ({
        todos: [],
        newTodo: null,
    }),

    mounted() {
        if (localStorage.getItem('todos')) {
            try {
                this.todos = JSON.parse(localStorage.getItem('todos'))
            } catch (e) {
                localStorage.removeItem('todos')
            }
        }
    },

    methods: {
        addTodo() {
            if (!this.newTodo) {
                return
            }

            this.todos.push(this.newTodo)
            this.newTodo = ''
            this.saveTodo()
        },

        removeTodo(todo) {
            this.todos.splice(this.todos.indexOf(todo), 1)
        },

        saveTodo() {
            let parsed = JSON.stringify(this.todos)
            localStorage.setItem('todos', parsed)
        },
    },

    computed: {
        totalToDos() {
            return this.todos.length + ' ' + 'left'
        },
    },
}
</script>

<style lang="scss">
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
        background-color: #ff6b6b;
        border-top-right-radius: 8px;
        border-top-left-radius: 8px;
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
                border-radius: 4px;
                border: none;
                padding: 5px 20px;
                box-shadow: inset 0px 1px 3px rgba(28, 33, 34, 0.25);

                &:focus {
                    box-shadow: 0 0 2px 2px #4ecdc4;
                    outline: 0;
                }
            }

            & .add-btn {
                width: 40px;
                height: 40px;
                background-color: #f7fff7;
                position: relative;
                border: none;
                transition: all 0.3s ease;
                border-radius: 100%;
                cursor: pointer;
                box-shadow: 0px 0px 2px rgba(0, 0, 0, 0.25);

                &::before,
                &::after {
                    content: '';
                    position: absolute;
                    width: 3px;
                    height: 50%;
                    background-color: #1c2122;
                    border-radius: 2px;
                    top: 26%;
                    left: 47%;
                }

                &::after {
                    transform: rotate(-90deg);
                }

                &:hover {
                    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.5);

                    &::before,
                    &::after {
                        background-color: #4ecdc4;
                    }
                }
            }
        }

        & .heading {
            color: #f0f3f5;
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
            background-color: #eee8db;
            transition: background-color 0.3s ease;
            position: relative;
            padding: 5px;

            &:hover {
                background-color: #bebebe;

                & button.close-btn {
                    opacity: 1;

                    &::before,
                    &::after {
                        background-color: #ff6b6b;
                    }
                }
            }

            &:nth-child(odd) {
                background-color: #f0f3f5;
                &:hover {
                    background-color: #bebebe;
                }
            }

            & button.close-btn {
                height: 100%;
                background-color: transparent;
                position: absolute;
                border: none;
                opacity: 0.3;
                transition: all 0.3s ease;
                right: 10px;
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
        background-color: #ff6b6b;
        border-bottom-right-radius: 8px;
        border-bottom-left-radius: 8px;
        display: flex;
        gap: 30px;

        & .todo-info {
            color: white;
        }
    }
}
</style>
