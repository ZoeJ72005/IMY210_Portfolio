<template>
  <div>
    <form
      v-if="!submitted"
      name="contact"
      method="POST"
      netlify
      :action="formAction"
    >
      <input type="hidden" name="form-name" value="contact" />

      <p>
        <label>Name <input type="text" name="name" required /></label>
      </p>
      <p>
        <label>Email <input type="email" name="email" required /></label>
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
const formAction = ref("?success=true")

onMounted(() => {
  const query = new URLSearchParams(window.location.search)
  if (query.get("success") === "true") {
    submitted.value = true
    window.history.replaceState({}, document.title, window.location.pathname)
  }
})
</script>

<style scoped>
.confirmation {
  margin: 2rem auto;
  max-width: 500px;
  background: #e6fffa;
  border: 2px solid #38b2ac;
  padding: 1.5rem;
  border-radius: 1rem;
  text-align: center;
  color: #234e52;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
}
</style>
