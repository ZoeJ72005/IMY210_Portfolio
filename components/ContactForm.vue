<template>
  <div>
    <div v-if="submitted" class="confirmation">
      <h2>🌸 Thank you!</h2>
      <p>Your message was sent successfully.</p>
    </div>

    <form
      v-else
      name="contact"
      method="POST"
      netlify
      netlify-honeypot="bot-field"
      :action="formAction"
      class="form-box"
    >
      <input type="hidden" name="form-name" value="contact" />
      <p style="display: none">
        <label>Don’t fill this out if you're human: <input name="bot-field" /></label>
      </p>

      <p>
        <label>Your Name<br />
          <input type="text" name="name" class="input-field" required />
        </label>
      </p>
      <p>
        <label>Your Email<br />
          <input type="email" name="email" class="input-field" required />
        </label>
      </p>
      <p>
        <label>Message<br />
          <textarea name="message" class="textarea-field" required></textarea>
        </label>
      </p>
      <p>
        <button type="submit" class="submit-btn">Send</button>
      </p>
    </form>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const submitted = ref(false)

// Netlify doesn't support AJAX by default, so we rely on a redirect-free workaround:
const formAction = ref("?success=true")

onMounted(() => {
  const query = new URLSearchParams(window.location.search)
  if (query.get("success") === "true") {
    submitted.value = true
    // Clean the URL after showing success
    window.history.replaceState({}, document.title, window.location.pathname)
  }
})
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

.confirmation {
  text-align: center;
  padding: 2rem;
  background: #ffeaf4;
  border-radius: 1.5rem;
  max-width: 500px;
  margin: 2rem auto;
  color: #4b0082;
  box-shadow: 0 0 15px rgba(192, 132, 252, 0.2);
}
</style>
