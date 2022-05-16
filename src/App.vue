<template>

  <div id="app">
    <h1> Welcome to Opportunity</h1>
    <h2> 16.05.22 </h2>

      <ul class="ul">

        <li class="li">
          <span style="color:red">14.00Uhr</span>
            <h3> Besichtigungs Besuch </h3>
              <span> Interessierte fuer den zweiten Kurs werden uns besuchen </span>
        </li>      

        <li class="li">
          <span style="color:red">14.00Uhr</span>
            <h3> Besichtigungs Besuch </h3>
              <span> Interessierte fuer den zweiten Kurs werden uns besuchen </span>
        </li> 

        <li class="li">
          <span style="color:red">14.00Uhr</span>
            <h3> Besichtigungs Besuch </h3>
              <span> Interessierte fuer den zweiten Kurs werden uns besuchen </span>
        </li> 

      </ul>

    <footer>
      <img class="img-footer" alt="logo" src="./assets/STZH_SEB_Logo.png">
      <img class="img-footer2" alt="logo" src="./assets/Opportunity.png">
      <img class="img-footer3" alt="logo" src="./assets/SAG_Logo_De.png">
    </footer>
  </div>

</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
