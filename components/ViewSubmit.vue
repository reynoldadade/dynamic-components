<template>
  <div class="w-full">
    <div>
      <div class="p-2 border rounded m-1">Name: {{ personal.name }}</div>
      <div class="p-2 border rounded m-1">DOB: {{ personal.date }}</div>
      <div class="p-2 border rounded m-1">Email: {{ personal.email }}</div>
      <div class="p-2 border rounded m-1">ID: {{ personal.id }}</div>
    </div>
    <div>
      <div class="p-2 border rounded m-1">
        Organization: {{ work.companyName }}
      </div>
      <div class="p-2 border rounded m-1">Role: {{ work.role }}</div>
      <div class="p-2 border rounded m-1">Email: {{ work.email }}</div>
      <div class="p-2 border rounded m-1">Address: {{ work.address }}</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    work: {
      type: Object,
      default: () => {},
    },
    personal: {
      type: Object,
      default: () => {},
    },
  },
}
</script>

<style></style>
