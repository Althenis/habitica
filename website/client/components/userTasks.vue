<template lang="pug">
.row
  .col(v-for="taskType in tasksTypes")
    h3 {{taskType}}s
    ul
      task(v-for="task in tasks", v-if="task.type === taskType", :key="task.id", :task="task")
</template>

<script>
import Task from './task';
import { mapState } from 'client/libs/store';

export default {
  components: {
    Task,
  },
  data () {
    return {
      tasksTypes: ['habit', 'daily', 'todo', 'reward'],
    };
  },
  computed: {
    ...mapState({tasks: 'tasks.data'}),
  },
};
</script>