<template>
  <div id="app">
    <Conversor moeda-a="USD" moeda-b="BRL"/>
  </div>
</template>

<script>
import Conversor from "./components/Conversor.vue"
export default 
{
  name: "app",
  components:
  {
    Conversor
  }
}

</script>

<style>
body
{
    display: flex;
    background-image: url(assets/walpaper.jpg);
}
#app {
  font-family: 'Times New Roman', Times, serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  justify-content: center;
  align-items: center;
  margin: auto;
}
#app select 
{
  height: 30px;
  font-size: 17px;
}
#app .credit 
{
  font-size: 18px;
  color: rgb(3, 1, 121);
}
#app .credit strong
{
  font-style: italic;
    text-decoration: underline;
}
#app .credit strong:hover
{
  color: black;
  background-color: aliceblue;
}

</style>
