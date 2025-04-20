<template>
  <div>
    <form
      v-if="!submitted"
      name="contact"
      method="POST"
      data-netlify="true"
      netlify-honeypot="bot-field"
      :action="formAction"
    >
      <!-- Netlify hidden fields -->
      <input type="hidden" name="form-name" value="contact" />
      <p style="display:none">
        <label>Don’t fill this out: <input name="bot-field" /></label>
      </p>

      <p>
        <label>Your Name: <input type="text" name="name" required /></label>
      </p>
      <p>
        <label>Your Email: <input type="email" name="email" required /></label>
      </p>
      <p>
        <label>Your Role:
          <select name="role[]" multiple required>
            <option value="leader">Leader</option>
            <option value="follower">Follower</option>
          </select>
        </label>
      </p>
      <p>
        <label>Message: <textarea name="message" required></textarea></label>
      </p>
      <p>
        <button type="submit">Send</button>
      </p>
    </form>

    <div v-else class="confirmation">
      <h2>🎉 Thank you!</h2>
      <p>Your message has been successfully submitted.</p>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const submitted = ref(false)
const formAction = ref('?success=true')

onMounted(() => {
  const query = new URLSearchParams(window.location.search)
  if (query.get('success') === 'true') {
    submitted.value = true
    // Clean the URL
    window.history.replaceState({}, document.title, window.location.pathname)
  }
})
</script>

<style scoped>
.confirmation {
  margin: 2rem auto;
  max-width: 500px;
  background: #f0fff4;
  border: 2px solid #38a169;
  padding: 1.5rem;
  border-radius: 1rem;
  text-align: center;
  color: #22543d;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
}
</style>
