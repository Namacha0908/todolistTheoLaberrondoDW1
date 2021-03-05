<template>

    <div class="card">
        <div class="head">
            <p>{{date}}</p>
            <p class="headTitle">{{titre}}</p>
            <p v-if="tasks.length <= 1 ">{{tasks.length}} tâche</p>
            <p v-else>{{tasks.length}} tâches</p>
        </div>
        <NewTodo v-on:newTask="addTask" />
        <ToDoList v-bind:tasks="tasks" @made="doneOr" @remove="deleteTask" />
    </div>

</template>

<script>
import NewTodo from '@/components/NewTodo.vue'
import ToDoList from '@/components/ToDoList.vue'
export default {
  name: 'TodoCard',
  components: {
    NewTodo,
    ToDoList
  },
  data () {
    return {
      tasks: [],
      titre: "VueJs Tutorial ToDo List"
    }
  },
  computed: {
      date: function () {
                var todayDate = new Date()

              
                return `${todayDate.getDay()} / ${todayDate.getMonth() + 1 } / ${todayDate.getFullYear()}`;
            }
        

  },
  methods: {
      addTask(contenuTask){
            var newTask = {
                contenuTask: contenuTask,
                isDone: false
            }
            this.tasks.push(newTask)
      },

      doneOr(task){
          if(task.isDone){
              task.isDone = false
          }else{
              task.isDone = true
          }
      },
      
      deleteTask(task){
          let actualTask = this.tasks.indexOf(task)
          this.tasks.splice(actualTask, 1)
      }
  },
}
</script>

<style>
    .card{
        background-color: white;
        width: 100%;
        margin-top: 150px;
      
    }
    .headTitle {
        color: green;
    }
    .head{
        display: flex;
        justify-content: space-between;
        
        border-bottom: 2px solid rgba(0, 0, 0, 0.2)
    }
    
</style>