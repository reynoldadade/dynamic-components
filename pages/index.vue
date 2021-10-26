<template>
  <div class="w-full p-10 flex flex-col justify-center items-center">
    <div class="flex w-3/4">
      <button
        v-for="button in buttons"
        :key="button.name"
        class="flex-1 p-2 border"
        :class="{
          'bg-white text-blue-500': button.component !== currentComponent,
          'bg-blue-500 text-white': button.component === currentComponent,
        }"
        @click.prevent="setCurrentComponent(button.component)"
      >
        {{ button.name }}
      </button>
    </div>
    <div class="w-3/4">
      <Component :is="currentComponent" />
    </div>
  </div>
</template>

<script>
import Pending from '@/components/Pending.vue'
export default {
  components: {
    Pending,
  },
  data() {
    return {
      task: '',
      tasks: [],
      currentComponent: 'Pending',
      buttons: [
        { name: 'Pending', component: 'Pending' },
        { name: 'Completed', component: 'Completed' },
        { name: 'Deleted', component: 'Deleted' },
      ],
    }
  },
  methods: {
    setCurrentComponent(component) {
      this.currentComponent = component
    },
    addTask(task) {
      // use date as id
      const newTask = { name: task, id: Date.now(), status: 'pending' }
      this.tasks = [...this.tasks, newTask]
    },
    removeTask(task) {
      // filter by id
      this.tasks = this.tasks.filter((item) => item.id !== task.id)
    },
    markAsCompleted(task) {
      const completedTask = { ...task, completed: true }
      const filteredTasks = this.tasks.filter((item) => item.id !== task.id)
      this.tasks = [...filteredTasks, completedTask]
    },
  },
}
</script>
