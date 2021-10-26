<template>
  <div class="w-full p-10 flex flex-col justify-center items-center">
    <div class="p-2 w-1/2">
      <div class="flex">
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
      <div class="">
        <!-- keep state of components  -->
        <keep-alive>
          <Component
            :is="currentComponent"
            :personal="personal"
            :work="work"
            :save-personal-details="savePersonalDetails"
            :save-work-details="saveWorkDetails"
            :set-current-component="setCurrentComponent"
          />
        </keep-alive>
      </div>
    </div>
  </div>
</template>

<script>
import Personal from '@/components/Personal.vue'

export default {
  components: {
    Personal,
    Work: () => import('~/components/Work.vue'),
    ViewSubmit: () => import('~/components/ViewSubmit.vue'),
  },
  data() {
    return {
      currentComponent: 'Personal',
      buttons: [
        { name: 'Personal Details', component: 'Personal' },
        { name: 'Work Details', component: 'Work' },
        { name: 'View and Submit', component: 'ViewSubmit' },
      ],

      personal: {},
      work: {},
    }
  },
  methods: {
    setCurrentComponent(component) {
      this.currentComponent = component
    },
    saveWorkDetails(form) {
      this.work = form
      this.currentComponent = 'ViewSubmit'
    },
    savePersonalDetails(form) {
      this.personal = form
      this.currentComponent = 'Work'
    },
  },
}
</script>
