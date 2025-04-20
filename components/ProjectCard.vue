<template>
    <div class="card">
      <h2>{{ project.title }}</h2>
      <p>{{ project.description }}</p>
      <a :href="project.link" target="_blank">View Project</a>
    </div>
  </template>
  
  <script setup>
  defineProps(['project'])
  </script>
  
  <style scoped>
  .card {
    background: #fbe0f8;
    border-left: 6px solid #c084fc;
    padding: 1rem;
    border-radius: 1rem;
    transition: all 0.3s ease;
    box-shadow: 0 4px 8px rgba(240, 140, 200, 0.2);
  }
  
  .card:hover {
    transform: scale(1.02);
    box-shadow: 0 6px 14px rgba(192, 132, 252, 0.3);
  }
  
  a {
    color: #7e22ce;
    font-weight: bold;
    text-decoration: none;
    margin-top: 0.5rem;
    display: inline-block;
  }
  </style>
  