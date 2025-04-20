<template>
  <div class="app-wrapper">
    <header>
      <nav>
        <NuxtLink to="/">Home</NuxtLink>
        <NuxtLink to="/projects">Projects</NuxtLink>
        <NuxtLink to="/contact">Contact</NuxtLink>
      </nav>
    </header>
    <NuxtPage />
  </div>
</template>

<style scoped>
.app-wrapper {
  background: linear-gradient(to bottom, #ffeaf4, #f9e0f9);
  min-height: 100vh;
  font-family: 'Segoe UI', sans-serif;
  color: #4b0082;
}

header {
  background: linear-gradient(to right, #c084fc, #f472b6);
  padding: 1rem;
  text-align: center;
  border-bottom: 4px solid #f472b6;
}

nav {
  display: flex;
  justify-content: center;
  gap: 2rem;
}

a {
  color: white;
  font-weight: bold;
  text-decoration: none;
  font-size: 1.1rem;
}

a:hover {
  text-decoration: underline;
}
</style>
