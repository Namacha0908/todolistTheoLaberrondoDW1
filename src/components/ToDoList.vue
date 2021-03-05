<template>
<div class="taches">
    <div v-for="task in tasks" :key="task" class="tache">
        <input type="checkbox"  v-on:click="made(task)"/>
            <p v-bind:class="{done: task.isDone}">{{ task.contenuTask }}</p>
        <button v-on:click="deleteTask(task)" class="supp">-</button>
    </div>
</div>
</template>

<script>
export default {
  name: 'TodoList',

  props: ['tasks'],

  methods: {
      made(task){
          this.$emit('made', task)
      },
      deleteTask(task){
          this.$emit('remove', task)
      }
  }
}
</script>

<style>
    .taches{
        padding: 0 75px;
    }
    .tache{
        display: flex;
        justify-content: space-between;
        margin: 20px 0;
    }
    .done{
        text-decoration: wavy line-through rgb(82, 2, 187);

    }
    .supp{
        background-color: rgb(255, 0, 0);
        border: none;
       
        padding: 5px 5px;
        color:white;
    }
</style>