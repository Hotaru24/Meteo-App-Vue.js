<template>
  <div class="hello">
    <h1>{{ name }}</h1>
    <div class="data-body">
        <div class="appData">
          <p id="temp">{{temp}}°C</p>
          <p>Humidité : {{humidity}}%</p>
        </div>
        <div class="appData">
          <p>Vent : {{windSpeed}} km/h </p>
          <img 
            src='../assets/arrow.png'
            alt="logo" 
            v-bind:style="{transform: `rotate(${windDegree}deg)`, maxWidth: '80px'}"
          />
        </div>
        <img :id="weatherPic" v-bind:src='icon' v-bind:alt='layout'/>
      </div>
  </div>
</template>



<script>
import axios from 'axios';
export default {
  name: 'Weather',
  props: {
    msg: String
  },
  data: function (){
    return {
      name: '',
      icon:'',
      layout: '',
      temp: 0,
      humidity: 0,
      windSpeed: 0,
      windDegree: 0,
      apiKey: 'b2307c78a2534a93cbd29390deba0618'
    }
  },

    mounted: function () {
      navigator.geolocation.getCurrentPosition( (position) => {
      axios.get('http://api.openweathermap.org/data/2.5/weather?lat=' + position.coords.latitude + '&lon=' + position.coords.longitude + '&units=metric&appid=' + this.apiKey)
        .then((result) => {
          console.log(result.data.name)
          this.name = result.data.name,
          this.icon = 'https://openweathermap.org/img/wn/' + result.data.weather[0].icon + '@2x.png', 
          this.layout = result.data.weather[0].description
          this.temp = result.data.main.temp,
          this.humidity = result.data.main.humidity,
          this.windSpeed = Math.round(result.data.wind.speed*3.6)
          this.windDegree = result.data.wind.deg
        })
        .catch( (error) => {
            console.log("Erreur ! Impossible d'accéder à l'API." + error)
        })
      }, console.log("err") );
    }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.data-body{
  display: flex;
}

h2{
  font-size: 4em;
}

.appData{
  margin: 0 30px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

#temp{
  font-size: 2em;
  margin: 0;
}

#weatherPic{
  height: 240px;
  width: 240px;
}
</style>
