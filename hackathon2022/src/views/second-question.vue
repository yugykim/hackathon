<template>
  <div class="second">
    <div class="container">
      <div class="second-qustion-box">
        <h1>{{ name }} Please, tell me what made your feelling.</h1>
      </div>
      <div class="imgbox">
        <img src="../img/c-img1.gif" class="c-img" />
      </div>
      <div class="button">
        <selectbutton
          v-for="emotion in emotions"
          :key="emotion"
          :emotion="emotion"
          v-on:change="changeColor"
        />
      </div>
    </div>
    <div class="button">
      <router-link to="/third-question">
        <HelloWorld msg=">" />
      </router-link>
      <router-view />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import selectbutton from "@/components/selectbutton.vue";
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Second",
  components: {
    selectbutton,
    HelloWorld,
  },
  data() {
    return {
      name: localStorage.username,
      emotions: [
        { type: "WORK", answer: false },
        { type: "STUDY", answer: false },
        { type: "RELAXING", answer: false },
        { type: "MUSIC", answer: false },
        { type: "FOOD", answer: false },
        { type: "FRIENDS", answer: false },
        { type: "FRIENDS", answer: false },
      ],
    };
  },
  methods: {
    changeColor: function (emotion) {
      emotion.answer = !emotion.answer;
    },
  },
};
</script>

<style scoped>
.second {
  box-sizing: border-box;
  height: 100vh;
  background: url("../img/bg-1.gif");
  background-size: 100%;
  display: flex;
  background-size: cover;
}

.container {
  display: flex;
  flex-direction: column;
  margin: auto;
  padding-left: 28%;
}

.second-qustion-box {
  text-align: center;
  flex: 4;
  width: 40rem;
  margin: auto;
}
.imgbox {
  margin: auto;
  display: flex;
  align-items: center;
}
.c-img {
  width: 20rem;
}

.button {
  display: flex;
  flex: 2;
  margin: auto;
  text-align: center;
  max-width: 30rem;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
