<script>
import { ref } from 'vue'
export default {
  setup() {
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
  <div>
    <h1>Composition Form</h1>
    <hr />
    <form @submit.prevent="submitForm">
      <div class="form-group">
        <label for="name">Name:</label>
        <input type="text" id="name" v-model="formData.name" />
        <span class="error" v-if="errors.name && !formData.name">{{ errors.name }}</span>
      </div>
      <div class="form-group">
        <label for="country">Country:</label>
        <select id="country" v-model="formData.country">
          <option value="usa">USA</option>
          <option value="india">India</option>
          <option value="uk">UK</option>
        </select>
        <span class="error" v-if="errors.country && !formData.country">{{ errors.country }}</span>
      </div>
      <div class="form-group">
        <label for="messaage">Message:</label>
        <textarea rows="4" cols="50" id="message" v-model="formData.message"></textarea>
        <div class="error" v-if="errors.message">{{ errors.message }}</div>
      </div>
      <div class="form-group">
        <label for="mailNotification">Get notification at mail:</label>
        <input type="checkbox" id="mailNotification" v-model="formData.mailNotification" />
      </div>
      
      <button class="button" type="submit">Submit</button>
    </form>
  </div>
</template>


<style scoped>
.form {
  width: 300px;
  margin: 10 auto;
  padding: 30px;
  border: 1px solid #ccc;
  border-radius: 5px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
}

.form-group {
  margin-bottom: 15px;
}
.button {
  background-color: #008cba;
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
}

label {
  display: block;
  font-weight: bold;
}

input[type='text'],
select {
  width: 100%;
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 3px;
}

.error {
  color: red;
}
</style>
