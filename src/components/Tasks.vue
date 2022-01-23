<template>
    <div v-for="task in tasks" :key="task.id">
        <Task @toggle-reminder="$emit('toggle-reminder', task.id)" :task="task" @delete-task="$emit('delete-task', task.id)" />
    </div>
</template>

<script>
    import Task from './Task.vue';

    export default {
        name: 'Tasks',

        props: {
            tasks: Array,
        },

        components: {
            Task,
        },

        emits: ['delete-task', 'toggle-reminder'],
    }
</script>

<style></style>