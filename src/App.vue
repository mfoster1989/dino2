<template>
  <div id="app">
      <TheHeader/>
        <main>
          <h2>Profiles</h2>
            <ul>
             <li> <TheProfile v-for="dinosaur in dinosaursData" v-bind:dinosaur="dinosaur" :key="dinosaur.name" /></li>
            </ul>
        </main>
      <TheFooter/>
  </div>
</template>

<script>
import TheHeader from "./components/TheHeader"
import TheProfile from "./components/TheProfile"
import TheSkillList from "./components/TheSkillList"
import TheFooter from "./components/TheFooter"

export default {
  name: "App",
  data() {
    return {
      dinosaursData: [],
      apiURL: "../static/dinosaurs.json"
    }
  },
  components: {
    TheHeader,
    TheProfile,
    TheSkillList,
    TheFooter
  },
  mounted() {
    fetch(this.apiURL)
    .then(response => response.json())
    .then(response => {
      this.dinosaursData = response
    })
  }
}
</script>

<style scoped>
html {
	margin: 0;
	padding: 0;
}
ul {
  list-style: none;
}
body {
	margin: 0 30px 0 30px;
	padding: 0;
	font-family: sans-serif;
	color: #1b997a;
	display: grid;
	grid-template-rows: 15% 75% 10%;
}
main {
  grid-row: 2/3;
}
main section {
  padding: 0 20px 0 20px;
  display: grid;
  grid-template-columns: repeat(auto-fit, x100%);
  grid-gap: 10px;
  margin: 0 auto;
  width: 50%;
}

small {
  color: black;
  font-size: .5rem;
  margin-left: 10px;
}
p {
  font-size: .8rem;
}
</style>
