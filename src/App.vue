<template>
  <section id="app">
    <main>
      <form class="search-box">
          <input type="text" 
                 class="search-bar" 
                 placeholder="Search..." />
      </form>
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
</style>
