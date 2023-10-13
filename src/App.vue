<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header class="d-flex flex-wrap justify-content-center py-3" style="width: 100%;  background-color: rgba(255, 255, 255, 0.8);">
        <RouterLink to="/" class="d-flex align-items-center mb-3 mb-md-0 me-md-auto link-body-emphasis text-decoration-none">
        <svg class="bi me-2" width="50" height="70"></svg>
        <span class="fs-3" style="color: black; " ><h2>พยากรณ์อากาศ</h2></span>
        </RouterLink>
        <ul class="nav col-12 col-lg-auto my-2 justify-content-center my-md-0 text-small ">
            <li>
              <RouterLink to="/weather" class="nav-link text-white" style="color: aqua;"> 
                  <img class="bi d-block mx-auto mb-1" src="@/assets/weather_head.png" alt="cart" width="24" height="24" >
                  <p style="color:rgb(74, 75, 77) ;">ข้อมูล</p>
              </RouterLink>
            </li>
        </ul>
    </header>

    <div class="mainbd">
      <RouterView />
    </div>
    
    
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Kanit:wght@500;600&display=swap');

body{
    background: #D4E2D4;
    font-family: 'Kanit', sans-serif;
}

p {
  margin: 0%;
}
</style>

