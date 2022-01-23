<template>
    <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
        <h3>
            {{ task.text }}
            <!-- <i class="fas fa-times" @click="onDelete(task.id)"></i> -->
            <i class="fas fa-times" @click="$emit('delete-task', task.id)"></i>
        </h3>
        <p>{{ task.day }}</p>
    </div>
</template>

<script>
    export default {
        name: 'Task',

        props: {
            task: Object
        },

        methods: {
            /* onDelete(id){
                this.$emit('delete-task', id);
            } */
        }
    }
</script>

<style scoped>
    .task{
        background: #f4f4f4;
        margin: 4px;
        padding: 10px 20px;
        cursor: pointer;
    }
    .task.reminder{
        border-left: 5px solid green;
    }
    .task h3{
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    .fas{
        color: red;
    }
</style>