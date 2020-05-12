<template>
  <section id="app">
    <main>
      <section class="all-info">
          <form class="search-box" @submit="preventSubmit">
              <input type="text" 
                    class="search-bar" 
                    placeholder="Search..." 
                    v-model="query"
                    @keypress="fetchWeather"
              />
          </form>
          <section class="weather-wrap" v-if="typeof weather.main != 'undefined'">
              <section class="location-box">
                <h1 class="location">{{ weather.name }}, {{ weather.sys.country }} </h1>
                <h2 class="date">{{ currentDate() }}</h2>
              </section>

              <section class="weather-box">
                  <div class="temp">{{ Math.round(weather.main.temp) }}°c</div>
                  <div class="weather">{{ weather.weather[0].description }}</div>
              </section>
          </section>
      </section>
    </main>
  </section>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      api_key: 'c117c79223f634582cd813b812d3e14b',
      url_base: 'https://api.openweathermap.org/data/2.5/',
      query: '',
      weather: {}
    }
  },
  methods : {
    fetchWeather (e) {
      if(e.key == 'Enter') {
        fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
          .then(res => res.json())
          .then(results => this.weather = results)
          .catch(err => console.log(err.message))
      }
    },

    preventSubmit (e) {
      e.preventDefault();
    },

    currentDate () {
      let newDate = new Date();

      let months = ["January","February","March","April","May","June","July",
            "August","September","October","November","December"];
      
      let days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];

      let day = days[newDate.getDay()];
      let date = newDate.getDate();
      let month = months[newDate.getMonth()];
      let year = newDate.getFullYear();

      return `${day} ${date} ${month} ${year}`;

    }
  }
}
</script>

<style>

  * {
    box-sizing: border-box;
    padding: 0;
    margin: 0;
  }

  body {
    font-family: 'montserrat', sans-serif;
  }

  /* add background images to assets to target later */
  #app {
    transition: 0.4s;
  }

  main {
    min-height: 100vh;
    padding: 25px;
    background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.25), rgba(0, 0, 0, 0.75));
  }

  .all-info {
    width: 50%;
    margin: 5em auto;
  }

  .search-box {
    width: 100%;
    margin-bottom: 30px;
  }

  .search-bar {
    display: block;
    width: 100%;
    padding: 15px;
    color: #313131;
    font-size: 20px;
    appearance: none;
    border: none;
    outline-color: rgb(141, 57, 189);
    background: none;
    background-color: rgba(255, 255, 255, 0.15);
    border-radius: 0px 16px 0px 16px;
    transition: 0.4s;
    box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
  }

  .search-bar:focus {
     background-color: rgba(255, 255, 255, 0.75);
     box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
     border-radius: 16px 0px 16px 0px;
  }

  .location {
    font-size: 20px;
    text-align: center;
    text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
    font-weight: 500;
    color: white;
    font-size: 4em;
  }

  .date {
    font-size: 20px;
    text-align: center;
    font-weight: 300;
    color: white;
    margin: 10px;
  }

  .weather-box {
    text-align: center;
  }

  .temp {
    display: inline;
    padding: 10px 25px;
    color: white;
    font-size: 102px;
    font-weight: 900;
    text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
    background-color: rgba(255, 255, 255, 0.25);
    border-radius: 15px;
    margin: 30px 0px;
  }

  .weather {
    margin: 15px;
    color: white;
    font-size: 48px;
    font-weight: 700 italic;
    font-style: italic;
    text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  }
</style>
