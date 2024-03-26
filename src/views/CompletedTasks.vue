<template>
  <div>
    <div v-for="task in tasks" :key="task.name" class="task-item">
      <div class="task-name">{{ task.name }}</div>
      <div class="task-description">{{ task.description }}</div>
      <div class="task-deadline">{{ task.deadline }}</div>
      <button @click="markAsDone(task)" class="done-button">Mark as Done</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    tasks: {
      type: Array,
      default: () => []
    }
  },
  methods: {
    markAsDone(task) {
      console.log('Mark as done:', task);
      this.$emit('mark-as-done', task); // Emitting event to parent component
    }
  }
};
</script>