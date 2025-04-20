<template>
  <form name="contact" netlify class="form-box">
    <p>
      <label>Name<br />
        <input type="text" name="name" class="input-field" required />
      </label>
    </p>
    <p>
      <label>Email<br />
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
</template>

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
</style>
