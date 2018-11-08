<template>
  <div id="app">
    <header>
    </header>
    <main>

      <router-view></router-view>
    </main>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style>
body {
  margin: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

main {
  text-align: center;
  margin-top: 40px;
  background-image: url('../static/img/dota-backg.jpg');
}

header {
  margin: 0;
  height: 300px;
  padding: 0 16px 0 24px;
  background-image: url('../static/img/dota-banner.jpg');
  color: #ffffff;
}

header span {
  display: block;
  position: relative;
  font-size: 20px;
  line-height: 1;
  letter-spacing: .02em;
  font-weight: 400;
  box-sizing: border-box;
  padding-top: 16px;
  /*background: red;*/
}
</style>
