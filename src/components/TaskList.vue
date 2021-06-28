<template>
    <ul>
        <li
            v-for="(task, index) in tasks"
            :key="index"
            :class="{ completed: task.completed }">
            {{ task.title }}
        </li>
        <input type="text"
               placeholder="Agregar una nueva tarea..."
               v-model="title"
               @keyup.enter="add()">
    </ul>
</template>

<script>
export default {
    name: 'task-list',
    props: {
        listId: String,
        tasks: Array
    },
    data() {
        return {
            title: ''
        }
    },
    methods: {
        add() {
            //TODO implementar evento
        }
    }
}
</script>

<style lang="scss" scoped>
    ul {
        list-style: none;
        margin: 0;
        padding: 0;
    }
    li {
        background-color: #fafafa;
        border-radius: 3px;
        border-bottom: 1px solid #ccc;
        margin: 0.25rem 0;
        padding: 1rem;
        &.completed {
            background-color: #cfd8dc;
            color: #90a4ae;
        }
    }
    input {
            box-sizing: border-box;
            background-color: transparent;
            border:  2px solid transparent;
            border-radius: 3px;
            font-size: 1.1rem;
            outline: 0;
            padding: 0.5rem;
            transition: all 600ms ease;
            &:focus,
            &:active {
                background-color: #ffffff;
                color: #546e7a;
            }
            &::placeholder {
                color: #546e7a;
            }
        }
</style>