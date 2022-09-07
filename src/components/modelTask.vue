<template>
  <div class="modal">
    <div class="container">
      <close-button
        style="bottom: 90%; right: -10px"
        @click="$emit('closeModelTask')"
      />
      <h1>Task description</h1>
      <input type="text" :placeholder="placeholder" v-model="taskTitle" @keydown.enter="addTask" autofocus/>
      <button @click="addTask">Добавить</button>
    </div>
  </div>
</template>

<script>
import closeButton from "./UI/closeButton.vue";

export default {
  components: { closeButton },
  data(){
    return{
        placeholder: 'Enter the task',
        taskTitle: '',
    }
  },
  methods: {
    addTask(){
      if(this.taskTitle.length < 3){
        this.taskTitle = ''
        this.placeholder = 'Minimum of 3 characters'
        setTimeout(() => {this.placeholder = 'Enter the task'}, 3000) 
      } else {
        const task = {};
        task.title = this.taskTitle;
        task.checked = false

        this.$emit('addTask', task)

        this.taskTitle = ''
      }
    },
  }
};
</script>

<style scoped>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  padding: 20px;
  background: rgba(0, 0, 0, 0.5);
}

.container {
  position: fixed;
  z-index: 1;
  min-width: 280px;
  max-width: 400px;
  max-height: 400px;
  background: var(--bg-color-pink);
  padding: 20px;
  border-radius: 10px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

input {
  margin-top: 20px;
  display: block;
  width: 100%;
  height: calc(2.25rem + 2px);
  padding: 0.375rem 0.75rem;
  font-family: inherit;
  font-size: 1rem;
  font-weight: 400;
  line-height: 1.5;
  color: #212529;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #bdbdbd;
  border-radius: 0.25rem;
  transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
}

button {
  display: block;
  margin-top: 20px;
  font-weight: 700;
  color: white;
  text-decoration: none;
  padding: 0.8em 1em calc(0.8em + 3px);
  border-radius: 3px;
  background: rgb(64, 199, 129);
  box-shadow: 0 -3px rgb(53, 167, 110) inset;
  transition: 0.2s;
}
button {
  background: rgb(53, 167, 110);
}
button {
  background: rgb(33, 147, 90);
  box-shadow: 0 3px rgb(33, 147, 90) inset;
}
</style>
