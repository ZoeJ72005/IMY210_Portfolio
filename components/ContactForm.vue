<template>
    <form
      name="contact"
      method="POST"
      data-netlify="true"
      class="form-box"
    >
      <input type="hidden" name="form-name" value="contact" />
  
      <label>Name:</label>
      <input name="name" required class="input-field" />
  
      <label>Email:</label>
      <input name="email" type="email" required class="input-field" />
  
      <label>Message:</label>
      <textarea name="message" required class="textarea-field"></textarea>
  
      <button type="submit" class="submit-btn">Send</button>
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
  
  label {
    font-weight: bold;
    margin-top: 1rem;
    display: block;
    color: #4b0082;
  }
  
  .input-field,
  .textarea-field {
    width: 100%;
    padding: 0.75rem;
    border: none;
    border-radius: 1rem;
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
  