<script>
import { ref } from 'vue'
export default {
  setup() {
    // Form data Object
    const formData = ref({
      name: '',
      mailNotification: false,
      country: '',
      message: ''
    })

    const submitted = ref(false)
    const errors = ref({})

    function submitForm() {
      // Validate the form before submission
      if (!formData.value.name.trim()) {
        errors.value.name = 'Name is required'
        return
      }
      if (!formData.value.country) {
        errors.value.country = 'Country is required'
        return
      }
      if (!formData.value.message.trim()) {
        errors.value.message = 'Message is required'
        return
      }
      // Clear any previous errors
      errors.value = {}
      // Form is valid; proceed with submission
      submitted.value = true
      alert('From submitted successfully!')
    }
    return {
      formData,
      submitted,
      submitForm,
      errors
    }
  }
}
</script>

<template>
  <div class="center-box">
    <h1>Composition Form</h1>
    <form @submit.prevent="submitForm">
      <!-- Name Field -->
      <div class="form-group">
        <label for="name">Name:</label>
        <input type="text" id="name" v-model="formData.name" />
        <span class="error" v-if="errors.name && !formData.name">{{ errors.name }}</span>
      </div>
      <!-- Country Field -->
      <div class="form-group">
        <label for="country">Country:</label>
        <select id="country" v-model="formData.country">
          <option value="usa">USA</option>
          <option value="india">INDIA</option>
          <option value="uk">UK</option>
        </select>
        <span class="error" v-if="errors.country && !formData.country">{{ errors.country }}</span>
      </div>
      <!-- Message Field -->
      <div class="form-group">
        <label for="messaage">Message:</label>
        <textarea rows="4" cols="50" id="message" v-model="formData.message"></textarea>
        <div class="error" v-if="errors.message">{{ errors.message }}</div>
      </div>
      <!-- Get notification Field -->
      <div class="form-check">
        <label for="mailNotification">Get notification at mail:</label>
        <input type="checkbox" id="mailNotification" v-model="formData.mailNotification" />
      </div>
      <!-- Submit button -->
      <button class="button" type="submit">Submit</button>
    </form>
  </div>
</template>


<style scoped>
</style>
