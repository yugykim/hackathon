<template>
  <div class="spot-1">
    <div class="container">
      <div class="spot-1-question-box">
        <h1>This is your MOODSPOT.</h1>

        <div id="spotCard">
          <img v-if="spot.type === 'park'" src="../img/Verysad1.gif" alt="" />
          <img v-else-if="spot.type === 'cafe'" src="../img/Blue1.gif" alt="" />
          <img
            v-else-if="spot.type === 'recreation_center'"
            src="../img/Soso1.gif"
            alt=""
          />
          <img
            v-else-if="spot.type === 'restaurant'"
            src="../img/Good1.gif"
            alt=""
          />
          <img
            v-else-if="spot.type === 'finedining_restaurant'"
            src="../img/Happy1.gif"
            alt=""
          />

          <p>{{ spot.name }}</p>
          <br />
          <p>{{ spot.address }}</p>
          <br />
          <p>{{ spot.description }}</p>
          <br />
          <p>{{ spot.message }}</p>
          <br />
        </div>
      </div>
      <div class="button" type="submit">
        <router-link to="/spot-2">
          <spotBtn msg="Another Recommendation" />
        </router-link>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import spotBtn from "@/components/spotBtn.vue";
import axios from "axios";
export default {
  name: "spot-1",
  components: {
    spotBtn,
  },
  data() {
    return {
      spots: [],
      spot: "",
      url: "",
    };
  },
  async mounted() {
    const response = await axios.get("api/allspots");
    this.spots = response.data;
    this.spot = this.spots[0];
    console.log(this.spot);
    if (this.spot.type === "park") {
      this.url = "../img/Verysad-flanders_Park.gif";
    } else if (this.spot.type === "cafe") {
      this.url = "../img/Blue-alchemist_Inc.gif";
    } else if (this.spot.type === "recreation_center") {
      this.url = "../img/Soso-Glenmore_Sailing_School.gif";
    } else if (this.spot.type === "restaurant") {
      this.url = "../img/Good-Boogie.gif";
    } else if (this.spot.type === "finedining_restaurant") {
      this.url = "../img/Happy-Ari.gif";
    }
    console.log(this.url);
  },
  methods: {},
};
</script>

<style scoped>
.spot-1 {
  box-sizing: border-box;
  height: 100vh;
  background: url("../img/bg-1.gif");
  background-size: 100%;
  display: flex;
  justify-content: center;
  align-content: center;
}

.container {
  display: flex;
  flex-direction: column;
  margin: 4rem;
}

.spot-1-question-box {
  background-color: antiquewhite;
  text-align: center;
  flex: 4;
  width: 40rem;
  margin: auto;
}

.button {
  flex: 2;
  margin: 2rem;
  text-align: center;
}
</style>
