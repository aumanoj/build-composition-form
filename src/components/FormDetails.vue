<script setup>
const props = defineProps({
  formData: Object,
  required: true
})
</script>
<template>
  <div class="center-box">
    <h1>Form Data</h1>
    <div>Name: {{ formData?.name }}</div>
    <div>Country: {{ formData?.country }}</div>
    <div>Message: {{ formData?.message }}</div>
    <div>Get notification at mail: {{ formData?.mailNotification == true ? 'Yes' : 'No' }}</div>
  </div>
</template>

<style scoped></style>
