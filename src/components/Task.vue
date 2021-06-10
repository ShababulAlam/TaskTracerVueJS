<template>
<div @dblclick.prevent="handleTaskDBClick(task.id)" :class="[task.reminder ? 'reminder' : '', 'task', {'line-through': isLineThrough}]">
   <h3>{{task.text}}
       <i @click="$emit('delete-task',task.id)" class="fas fa-times-circle fa-lg"></i>
   </h3>
   <p>{{ task.day}} </p>

</div>
</template>

<script>
export default {
    name:'Task',
    data () {
      return {
        isLineThrough: false
      }
    },
    props:{
        task: Object
    },
    methods: {
      handleTaskDBClick(taskID) {
       
        this.isLineThrough = !this.isLineThrough
        this.$emit('toggle-reminder', taskID)
      }
    }
    
}
</script>



<style scoped>
.fas {
    display:flex;
  color: red;
  justify-content: flex-start;
  
}
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 5px 20px;
  cursor: pointer;
  background: rgba(255, 179, 80, 0.7);
  border-radius: 10px;
}
.task.reminder {
  border-left: 5px solid green;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.line-through {
  text-decoration: line-through;
}
</style>