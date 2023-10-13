<script setup>
import { RouterLink } from 'vue-router';
import { ref, watchEffect } from "vue";
import axios from "axios";
import { useWeatherStore } from '@/stores/weather';

const latitude = ref('18.89525429860656'); 
const longitude = ref('99.01108004859944'); 
const weatherStore = useWeatherStore();

watchEffect(() => {
  if (latitude.value && longitude.value) {
    showWeatherData();
  }
});

function WeatherData(url) {
  axios
    .get(url)
    .then((response) => {
      weatherStore.weatherData = response.data;
    })
    .catch((err) => {
      console.error(err);
    });
}

function showWeatherData() {
  const apiUrl = 'https://api.openweathermap.org/data/2.5/forecast';
  const apiKey = '4546b80f7b7b5d308f95442db543cb15';
  const lang = 'th';
  const units = 'metric';
  const url = `${apiUrl}?lat=${latitude.value}&lon=${longitude.value}&appid=${apiKey}&units=${units}&lang=${lang}`;
  WeatherData(url);
}



</script>

<template>
    <div class="frameoutline">
        <div class="frame">
            <div class="card text-center mb-3 mt-4" style="width: 80vw; margin: auto;  background-color:  rgba(255, 255, 255,0.8 );">
                <div class="card-body">
                    <img src="@/assets/weather-news.png" alt="cardimg" class="mb-3 mt-3" style="width: 30%;">
                    <h3 class="card-title">ค้นหาสภาพอากาศ 5 วัน</h3>
                    <div class="inputframe">
                        <div class="input-group" style="width: 70%; margin: auto;">
                            <span class="input-group-text">ละติจูดและลองจิจูด</span>
                            <input type="text" aria-label="latitude" class="form-control" id="lat" v-model="latitude" placeholder="latitude">
                            <input type="text" aria-label="longitude" class="form-control" id="long" v-model="longitude" placeholder="longitude">
                        </div>
                    </div>
                    <p class="card-text mt-2 mb-2">กรอกตำแหน่งที่ต้องการค้นหา</p>
                    <RouterLink to="/weather" class="btn btn-outline-dark" style="width: 50%;">ดูข้อมูล</RouterLink>
                </div>
            </div>
        </div>
    </div>

    
</template>

<script>



  


</script>



<style scoped>

body{
    margin: 0%;
    padding: 0%;
}

.frameoutline{
height: 100vh;
background-color: transparent;
}

.frame{
    display: flex;
    background-color: transparent;
}

.inputframe{
    display: flex;
}

</style>