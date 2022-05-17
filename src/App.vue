<template>
  <div id="app">
    <h1 class="title">{{title}}</h1>
    <h2>{{ currentDate() }}</h2>

    <ul class="ul">
      <li class="li">
        <span style="color: red">14.00Uhr</span>
        <h3>Besichtigungs Besuch</h3>
        <span> Interessierte fuer den zweiten Kurs werden uns besuchen </span>
      </li><br>

      <li class="li">
        <span style="color: red">14.00Uhr</span>
        <h3>Besichtigungs Besuch</h3>
        <span> Interessierte fuer den zweiten Kurs werden uns besuchen </span>
      </li><br>

      <li class="li">
        <span style="color: red">14.00Uhr</span>
        <h3>Besichtigungs Besuch</h3>
        <span> Interessierte fuer den zweiten Kurs werden uns besuchen </span>
      </li><br>
    </ul>

    <footer>
      <img class="img-footer" alt="logo" src="./assets/STZH_SEB_Logo.png" />
      <img class="img-footer2" alt="logo" src="./assets/Opportunity.png" />
      <img class="img-footer3" alt="logo" src="./assets/SAG_Logo_De.png" />
    </footer>
  </div>
</template>

<script>
import axios from "axios";
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  data() {
    return {
      date: new Date(),
      title: "Welcome to Opportunity",
      api_token:"AIzaSyA-qeDXOhEeQDA0vQf7LgkF7DQtGnAtmAU",
      sheet_id:"1a81aI0Y8ViZO0tI92h2YSMqVQJ8hmNNMyMylXgvwiU4",
      entries:[],

    };
  },
  computed: {
    gsheet_url(){
      return `https://sheets.googleapis.com/v4/spreadsheets/${this.sheet_id}/values:batchGet?ranges=A1%3AE100&valueRenderOption=FORMATTED_VALUE&key=${this.api_token}`;
    },
  },
  methods: {
    getData() {
      axios.get(this.gsheet_url).then((response) => {
        this.entries = response;
      },
    },

    currentDate() {
      const current = new Date();
      const day = current.getDate();
      const month = current.getMonth() + 1;
      const year = current.getFullYear();
      const dateTime = day + "." + month + "." + year;

      if (month < 10) {
        return day + "." + "0" + month + "." + year;
      }
      return dateTime;
    },
  },
};
</script>

<style>
body {
  background: #e8eff4;
}
#app {
  font-family: "Inter", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #323d4a;
  margin-top: 60px;
}

h1 {
  color: #323d4a;
  font-weight: 900;
  size: 62px;
  margin-left: 2rem;
}

h2 {
  color: #9aa7b1;
  font-weight: 500;
  size: 62px;
  margin-left: 2rem;
}

h3 {
  left: 4.35%;
  right: 13.49%;
  top: 20.33%;
  bottom: 20.33%;
  font-style: normal;
  font-weight: 900;
  font-size: 28px;
  line-height: 36px;
  color: #eb5e00;
}

span {
  left: 4.35%;
  right: 13.49%;
  top: 20.33%;
  bottom: 20.33%;
  font-style: normal;
  font-weight: 900;
  font-size: 28px;
  line-height: 36px;
  color: #eb5e00;
}

.ul {
  list-style-type: none;
  
}

.li {
  display: flex;
  flex-direction: column;
  width: 960px;
  height: 182px;
  background: #0f05a0;
}

footer {
  background: white;
  position: absolute;
  width: 1080px;
  height: 130px;
  left: 0px;
  top: 1790px;
}

.img-footer {
  position: absolute;
  width: 230px;
  height: 44px;
  left: 40px;
  top: 1833px;
}

.img-footer2 {
  position: absolute;
  width: 296px;
  height: 55px;
  left: 392px;
  top: 1828px;
}

.img-footer3 {
  position: absolute;
  width: 273px;
  height: 52px;
  left: 767px;
  top: 1829px;
}
</style>
