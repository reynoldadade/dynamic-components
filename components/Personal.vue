<template>
  <div class="w-full p-20">
    <form @submit.prevent="savePersonalDetails(form)">
      <div class="grid grid-cols-2">
        <div class="p-2">
          <label for="name">Name</label>
          <input
            id="name"
            v-model="form.name"
            type="text"
            class="p-2 rounded border w-full"
          />
        </div>
        <div class="p-2">
          <label for="date">DOB</label>
          <input
            id="date"
            v-model="form.date"
            type="date"
            class="p-2 rounded border w-full"
          />
        </div>
        <div class="p-2">
          <label for="amount">ID Number</label>
          <input
            id="id"
            v-model="form.id"
            type="text"
            class="p-2 rounded border w-full"
          />
        </div>
        <div class="p-2">
          <label for="email">Email</label>
          <input
            id="email"
            v-model="form.email"
            type="email"
            class="p-2 rounded border w-full"
          />
        </div>
      </div>
      <div class="p-2 m-2">
        <button class="p-2 w-full bg-green-500 text-white" type="submit">
          Save and Continue <i class="fas fa-arrow-right"></i>
        </button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  props: {
    savePersonalDetails: {
      type: Function,
      default: () => {},
    },
  },
  data() {
    return {
      form: {
        name: '',
        date: '',
        email: '',
        id: '',
      },
    }
  },
}
</script>

<style></style>
