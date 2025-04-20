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

    <div v-else>
      <p>✅ Thank you! Your message was sent.</p>
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
