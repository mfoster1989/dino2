<template>
  <section id="profiles">
    <li class="profile-card">
      <header class="profile-header" v-on:click="seen = !seen">
        <img :src="dinosaur.image" />
        <h2>{{dinosaur.name}}</h2>
      </header>
      <TheSkillList v-bind:dinosaur="dinosaur" :class="{hidden : seen}"></TheSkillList>
    </li>
  </section>
</template>
<script>

import TheSkillList from "./TheSkillList"

export default {
  name: "TheProfile",
  components: {
    TheSkillList
  },
  props: {
    dinosaur: {
      type: Object,
      required: true
    }
  },
  data() {
    return{
      seen: true
    }
  }
}
</script>
<style scoped>

.hidden {
  display: none
}

#profiles {
  list-style: none;
}

.profile-card {
  border-radius: 6px;
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.3);
  padding: 10px;
}

.profile-header {
  display: flex;
  flex-flow: row nowrap;
}

.profile-header img {
  width: 100px;
  height: 100px;
  border: 1px solid darkgrey;
  margin: 0 10px 0 10px;
}

</style>
