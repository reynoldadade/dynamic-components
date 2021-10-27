<template>
  <div class="w-full">
    <div class="w-full p-20">
      <form @submit.prevent="saveWorkDetails(form)">
        <div class="grid grid-cols-2">
          <div class="p-2">
            <label for="company_name">Company Name</label>
            <input
              id="company_name"
              v-model="form.companyName"
              type="text"
              class="p-2 rounded border w-full"
            />
          </div>
          <div class="p-2">
            <label for="role">Role</label>
            <input
              id="role"
              v-model="form.role"
              type="text"
              class="p-2 rounded border w-full"
            />
          </div>
          <div class="p-2">
            <label for="work_adresss">Address</label>
            <input
              id="work_adresss"
              v-model="form.address"
              type="text"
              class="p-2 rounded border w-full"
            />
          </div>
          <div class="p-2">
            <label for="work_email">Email</label>
            <input
              id="work_email"
              v-model="form.email"
              type="email"
              class="p-2 rounded border w-full"
            />
          </div>
        </div>
        <div class="p-2 m-2 flex">
          <button
            class="p-2 w-full bg-gray-400 text-white m-1"
            type="button"
            @click.prevent="setCurrentComponent('Personal')"
          >
            Previous <i class="fas fa-arrow-left"></i>
          </button>
          <button class="p-2 w-full bg-green-500 text-white m-1" type="submit">
            Save and continue <i class="fas fa-arrow-right"></i>
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    saveWorkDetails: {
      type: Function,
      default: () => {},
    },
    setCurrentComponent: {
      type: Function,
      default: () => {},
    },
  },
  data() {
    return {
      form: {
        companyName: '',
        role: '',
        email: '',
        address: '',
      },
    }
  },
}
</script>

<style></style>
