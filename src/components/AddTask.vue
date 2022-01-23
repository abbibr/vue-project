<template>
    <div>
        <form @submit="onSubmit" class="add-form">
            <div class="form-control">
                <label for="task">Task</label>
                <input type="text" v-model="text" id="task" name="text" placeholder="Add Task">
            </div>
            <div class="form-control">
                <label for="day">Date & Time</label>
                <input type="text" v-model="day" id="day" name="day" placeholder="Add Date & Time">
            </div>
            <div class="form-control form-control-check">
                <label>Check</label>
                <input type="checkbox" v-model="reminder" value="reminder">
            </div>
            <input type="submit" value="Save Task" class="btn btn-block">
        </form>
    </div>
</template>

<script>
    export default {
        name: 'AddTask',

        data() {
            return {
                text: '',
                day: '',
                reminder: false,
            }
        },
        methods: {
            onSubmit(e){
                e.preventDefault();

                if(!this.text){
                    alert('You must add the task!');
                }

                const newTask = {
                    id: Math.floor(Math.random() * 1000000),
                    text: this.text,
                    day: this.day,
                    reminder: this.reminder,
                };

                this.$emit('add-task', newTask);

                this.text = '';
                this.day = '';
                this.reminder = false;
            }
        }
    }
</script>

<style scoped>
    .add-form{
        margin-bottom: 40px;
    }
    .form-control{
        margin: 20px 0;
    }
    .form-control label{
        display: block;
    }
    .form-control input{
        width: 100%;
        height: 40px;
        margin: 5px;
        padding: 3px 7px;
        font-size: 17px;
    }
    .form-control-check{
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    .form-control-check label{
        flex: 1;
    }
    .form-control-check input{
        flex: 2;
        height: 20px;
    }
</style>