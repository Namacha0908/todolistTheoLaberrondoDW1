<template>
    <div class="ajout">
        <input class="latache" type="text" placeholder="Nouvelle tâche..." v-model="contenuTask" />
        <button class="send" v-on:click="addTask()">+</button>
    </div>
</template>

<script>
export default {
  name: 'new-todo',
  data () {
    return {
      contenuTask: ''
    }
  },
  methods: {
      addTask(){
          if(this.contenuTask != ''){
                this.$emit('newTask', this.contenuTask)
                this.contenuTask = ''
          }
      }
  }
}
</script>
<style>
    .ajout{
        display:flex;
        justify-content:center;
    }

    .latache {
        border: none;
        
    }
    .send{
        background-color: #00d0b2;
        width: 20px;
        height: 20px;
        border: none;
        border-radius: 30px;
        color: white;
    }
</style>