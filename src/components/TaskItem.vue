<template>
  <div>
    <div class="task-item">
      <h3>{{ task.name }}</h3>
      <p>{{ task.description }}</p>
      <p>Deadline: {{ task.deadline }}</p>
      <button @click="viewDetails">View Details</button>
      <button @click="removeTask">Remove</button>
    </div>

    <priority-task :priority-tasks="priorityTasks" @mark-as-done="moveToCompleted"></priority-task>
    <completed-task :tasks="completedTasks" @mark-as-done="moveToPriority"></completed-task>
  </div>
</template>

<script>
import PriorityTask from './prioritytask.vue';
import CompletedTask from './completedtask.vue';

export default {
  components: {
    PriorityTask,
    CompletedTask
  },
  data() {
    return {
      priorityTasks: [
        // Initialize with some initial priority tasks if needed
      ],
      completedTasks: [
        // Initialize with some initial completed tasks if needed
      ]
    };
  },
  methods: {
    moveToCompleted(task) {
      // Remove task from priorityTasks array
      const index = this.priorityTasks.findIndex(t => t === task);
      if (index !== -1) {
        this.priorityTasks.splice(index, 1);
        // Add task to completedTasks array
        this.completedTasks.push(task);
      }
    },
    moveToPriority(task) {
      // Remove task from completedTasks array
      const index = this.completedTasks.findIndex(t => t === task);
      if (index !== -1) {
        this.completedTasks.splice(index, 1);
        // Add task to priorityTasks array
        this.priorityTasks.push(task);
      }
    }
  }
};
</script>