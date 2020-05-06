<template>
  <section id="app">
    <main>
      <form class="search-box">
          <input type="text" 
                 class="search-bar" 
                 placeholder="Search..." />
      </form>

      <section class="weather-wrap">
           <section class="location">
             <h1 class="location"></h1>
             <h2 class="date"></h2>
           </section>

           <section class="weather-box">
              <div class="temp">°c</div>
              <div class="weather"></div>
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
      api_key: 'c117c79223f634582cd813b812d3e14b'
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
</style>
