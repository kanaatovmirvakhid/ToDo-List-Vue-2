<template>
  <h1>Today's tasks</h1>
  <div class="tasks">
    <div class="task completed" v-for="task of tasks" :key="task">
        <circle-checkbox :checked="task.checked" @click="task.checked = !task.checked" />
        <p :class="{textDecoration: task.checked}">{{task.title}}</p>
    </div>
  </div>
  <open-button style="bottom: 1%;right: 3%;" @returnTrue="modelTask = true"/>
  <model-task v-if="modelTask"
   @closeModelTask="modelTask = false"
   @addTask="appendTask"
   @mouseup.stop="closeModelTask($event)" />
</template>

<script>
import circleCheckbox from './components/UI/circleCheckbox.vue'
import openButton from './components/UI/openButton.vue'
import modelTask from './components/modelTask.vue'

export default {
  components: { circleCheckbox, openButton, modelTask},

  data(){
    return{
        modelTask: false,
        tasks: [{
            title: 'подцепи',
            checked: true,
        },]
    }
  },
  methods: {
    appendTask(task){
        this.tasks.push(task)

        localStorage.setItem('tasks', JSON.stringify(this.tasks))
    },
    closeModelTask(event){
      if(event.target.classList.contains('modal')){
        this.modelTask = false
      }
    }
  },
  mounted(){
    if(JSON.parse(localStorage.getItem('tasks'))){
    this.tasks = JSON.parse(localStorage.getItem('tasks'))
    }
  }
}
</script>

<style scoped>

</style>
