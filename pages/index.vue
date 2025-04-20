<template>
  <div class="home">
    <img src="assets/profile.jpg" alt="Profile photo" class="profile" />
    <h1>Zoë Joubert</h1>
    <p>Creative developer and designer who loves coding and colour 🌸</p>

    <div v-if="weather" class="weather-box">
      <h2>Current Weather in Pretoria</h2>
      <p>{{ weather.temperature }}°C – {{ weather.description }}</p>
    </div>

    <!-- Error Message -->
    <div v-if="error" class="error-message">
      <p>Oops! Something went wrong while fetching the weather data.</p>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const weather = ref(null);
const error = ref(false);

onMounted(async () => {
  try {
    const res = await fetch(`https://api.weatherstack.com/current?access_key=1c85ca7e4bca3361b511cea54fa55962&query=Pretoria`)
    if (!res.ok) {
      throw new Error('Network response was not ok');
    }
    const data = await res.json();
    weather.value = {
      temperature: data.current.temperature,
      description: data.current.weather_descriptions[0]
    };
  } catch (err) {
    error.value = true;
    console.error('Error fetching weather data:', err);
  }
});
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

.error-message {
  color: red;
  margin-top: 1rem;
  font-weight: bold;
}
</style>
