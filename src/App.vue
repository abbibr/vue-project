<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" title="Tasks" :showAddTask="showAddTask" />
    <div v-if="showAddTask">
          <AddTask @add-task="addTask" />
    </div>
    <Tasks @toggle-reminder="toggleReminder" :tasks="tasks" @delete-task="deleteTask" />
  </div>
</template>

<script>
  import Header from './components/Header.vue';
  import Tasks from './components/Tasks.vue';
  import AddTask from './components/AddTask.vue';

  export default {
    name: 'App',

    components: {
      Header, Tasks, AddTask,
    },

    data() {
      return {
        tasks: [],
        showAddTask: false,
      }
    },
    methods: {
      deleteTask(id){
        if(confirm('Do you delete this task?')){
          this.tasks = this.tasks.filter((task) => task.id !== id);
        }
      },
      toggleReminder(id){
        this.tasks = this.tasks.map((task) => task.id == id ? 
          {...task, reminder: !task.reminder} : task );
      },
      addTask(get){
        this.tasks = [...this.tasks, get];
      },
      toggleAddTask(){
        this.showAddTask = !this.showAddTask;
      }
    },
    created(){
      this.tasks = [
        {
          id: 1,
          text: 'Liverpool was created',
          day: 'march 1st march 1989',
          reminder: true
        },
        {
          id: 2,
          text: 'Manchester City was created',
          day: 'october 2nd may 1990',
          reminder: true
        },
        {
          id: 3,
          text: 'Chelsea was created',
          day: 'may 3rd may 1965',
          reminder: false
        }
      ];
    }

  }
</script>

<style>

  body{
    font-family: sans-serif;
  }
  .container{
    max-width: 500px;
    margin: 30px auto;
    overflow: auto;
    min-height: 100px;
    border: 1px solid steelblue;
    padding: 30px;
    border-radius: 5px;
  }
  .btn{
    display: inline-block;
    background: #000;
    color: #fff;
    border: none;
    padding: 12px 18px;
    margin: 5px;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 15px;
    font-family: inherit;
  }
  .btn:focus{
    outline: none;
  }
  .btn:active{
    transform: scale(0.98);
  }
  .btn-block{
    display: block;
    width: 100%;
  }

</style>
