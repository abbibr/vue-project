<template>
    <div>
        <header>
            <h1>{{ title }}</h1>
            <Button @toggle-add-task="$emit('toggle-add-task')" :text="showAddTask ? 'Remove Task' : 'Add Task' " :color="showAddTask ? 'crimson' : 'green' " />
        </header>
    </div>
</template>

<script>
    import Button from './Button.vue';

    export default {
        name: 'Header',

        // props: ['title'],
        props: {
            title: String,
            showAddTask: Boolean,
        },

        components: {
            Button,
        }
    }
</script>

<style>
    header{
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }
</style>