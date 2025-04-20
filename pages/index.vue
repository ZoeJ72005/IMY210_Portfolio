<template>
    <div class="home">
      <img src="assets/profile.jpg" alt="Profile photo" class="profile" />
      <h1>Zoë Joubert</h1>
      <p>Creative developer and designer who loves coding and colour 🌸</p>
  
      <div v-if="weather" class="weather-box">
        <h2>Current Weather in Pretoria</h2>
        <p>{{ weather.temperature }}°C – {{ weather.description }}</p>
      </div>
    </div>
  </template>
  
  <script setup>
  const weather = ref(null)
  const config = useRuntimeConfig()
  
  onMounted(async () => {
    const res = await fetch(`http://api.weatherstack.com/current?access_key=1c85ca7e4bca3361b511cea54fa55962&query=Pretoria`)
    const data = await res.json()
    weather.value = {
      temperature: data.current.temperature,
      description: data.current.weather_descriptions[0]
    }
  })
  </script>
  
  <style scoped>
  .home {
    text-align: center;
    padding: 2rem;
  }
  
  .profile {
    width: 150px;
    height: 150px;
    border-radius: 50%;
    border: 5px solid #f472b6;
    margin-bottom: 1rem;
  }
  
  .weather-box {
    background: #2bd7ee;
    border-left: 5px solid #c084fc;
    padding: 1rem;
    border-radius: 1rem;
    margin-top: 2rem;
    display: inline-block;
  }
  </style>
  