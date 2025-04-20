<template>
  <div id="app">
    <form
      name="contact"
      method="POST"
      netlify
      class="form-box"
      action="/success"
      @submit.prevent="handleSubmit"
    >
      <p>
        <label>Your Name<br />
          <input type="text" name="name" class="input-field" required v-model="form.name" />
        </label>
      </p>
      <p>
        <label>Your Email<br />
          <input type="email" name="email" class="input-field" required v-model="form.email" />
        </label>
      </p>
      <p>
        <label>Message<br />
          <textarea name="message" class="textarea-field" required v-model="form.message"></textarea>
        </label>
      </p>
      <p>
        <button type="submit" class="submit-btn">Send</button>
      </p>
    </form>

    <!-- Confirmation message after form submission -->
    <p v-if="isSubmitted" class="confirmation-message">Your message has been sent! Thank you.</p>
  </div>
</template>

<script>
export default {
  name: "ContactForm",
  data() {
    return {
      form: {
        name: '',
        email: '',
        message: ''
      },
      isSubmitted: false
    };
  },
  methods: {
    handleSubmit() {
      // Simulate form submission
      this.isSubmitted = true;
      // Clear the form fields after submission
      this.form.name = '';
      this.form.email = '';
      this.form.message = '';
      
      // If you're using Netlify, it will handle the form submission on the backend
      // You can perform additional actions here if needed (e.g., resetting the form on success).
    }
  }
};
</script>

<style scoped>
.form-box {
  background: linear-gradient(to bottom right, #fbc2eb, #a6c1ee);
  padding: 2rem;
  border-radius: 1.5rem;
  max-width: 500px;
  margin: 2rem auto;
  box-shadow: 0 5px 20px rgba(255, 0, 144, 0.2);
}

.input-field,
.textarea-field {
  width: 100%;
  padding: 0.75rem;
  border: none;
  border-radius: 1rem;
  margin-top: 0.5rem;
  margin-bottom: 1rem;
  font-size: 1rem;
  background-color: #fff0f6;
}

.input-field:focus,
.textarea-field:focus {
  outline: 2px solid #f472b6;
  background: #fffaff;
}

.submit-btn {
  background: #f472b6;
  color: white;
  padding: 0.75rem 1.5rem;
  border: none;
  font-weight: bold;
  font-size: 1rem;
  border-radius: 1rem;
  cursor: pointer;
  transition: all 0.3s;
}

.submit-btn:hover {
  background: #ec4899;
}

.confirmation-message {
  color: green;
  font-size: 1.2rem;
  text-align: center;
  margin-top: 1rem;
}
</style>
