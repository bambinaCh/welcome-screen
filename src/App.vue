<template>
  <div id="app">
    <h1 class="title">{{ title }}</h1>
    <h2 class="date">{{ currentDate() }}</h2>

    <ul class="ul">
      <li class="box" v-for="entry in entries.slice(1)" :key="entry">
        <span class="box-date">{{ entry[0] }} , {{ entry[1] }}</span
        ><br />
        <h3 class="box-title">{{ entry[2] }}</h3>
        <span class="box-text">{{ entry[3] }}</span>
      </li>
    </ul>

    <!-- <ul>
      <li>
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
    </ul> -->

    <footer>
      <img class="img" alt="logo" src="./assets/STZH_SEB_Logo.png" />
      <img class="img" alt="logo" src="./assets/Opportunity.png" />
      <img class="img" alt="logo" src="./assets/SAG_Logo_De.png" />
    </footer>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      date: new Date(),
      title: "Welcome to Opportunity",
      api_token: "AIzaSyA-qeDXOhEeQDA0vQf7LgkF7DQtGnAtmAU",
      sheet_id: "1a81aI0Y8ViZO0tI92h2YSMqVQJ8hmNNMyMylXgvwiU4",
      entries: [],
    };
  },
  computed: {
    gsheet_url() {
      return `https://sheets.googleapis.com/v4/spreadsheets/${this.sheet_id}/values:batchGet?ranges=A1%3AE100&valueRenderOption=FORMATTED_VALUE&key=${this.api_token}`;
    },
  },
  methods: {
    getData() {
      axios.get(this.gsheet_url).then((response) => {
        this.entries = response.data.valueRanges[0].values;
      });
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

  mounted() {
    this.getData();
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@500;900&display=swap");

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

.title {
  margin-left: 4rem;
  font-size: 4rem;
  margin-bottom: 1rem;
}

.date {
  margin-left: 4rem;
  font-size: 5rem;
  margin-top: 0;
  margin-bottom: 1rem;
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

.ul {
  list-style-type: none;
}

.box {
  width: 80%;
  height: 190px;
  padding: 2rem;
  margin: 25px;
  background: #0f05a0;
  padding-top: 60px;
  padding-bottom: 0;
}
.box-date {
  color: #eb5e00;
  font-weight: 900;
  font-size: 28px;
  margin-top: 1rem;
}

.box-title {
  color: #ffbaab;
  font-weight: 900;
  font-size: 28px;
  margin: 0;
}

.box-text {
  color: #ffbaab;
  font-size: 28px;
}

footer {
  display: flex;
  justify-content: space-between;
  box-sizing: border-box;
  position: fixed;
  width: 100%;
  left: 0;
  bottom: 0;
  padding: 20px;
  background: white;
}

.img {
  height: 50px;
}
</style>
