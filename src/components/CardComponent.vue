<template>
  <div class="photo" v-for="photo in api" :key="photo.id">
    <h2>Robot : {{ photo.rover.name }}</h2>
    <span class="camera_name">Camera : {{ photo.camera.full_name }}</span>
    <img :src="photo.img_src" alt="image" class="img_mars" />
    <span>{{ formatDate(photo.earth_date) }}</span>
    <br>
    <span> Status : {{ photo.rover.activity }}</span>
    <br>
    <span> Landing Date : {{ formatDate(photo.rover.landing_date) }}</span>
    <button @click="$emit('likeMars')">?</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "CardComponent",
  data: function () {
    return {
      api: "",
    };
  },
  created: function () {
    this.fetchData();
  },
  methods: {
    fetchData: async function () {
      const url = `https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&page=1&api_key=`;
      const token = "NJl7BrFTx7ZwbxWbm87IahtTMEtJa7DL65f9aTME";
      try {
        const res = await axios.get(url + token);
        this.api = res.data.photos;
        console.log(res.data.photos);
      } catch (error) {
        console.log(error);
      }
    },
    formatDate: function (date) {
      return new Date(Date.parse(date)).toLocaleDateString("fr-FR");
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
img {
  width: 300px;
  height: 250px;
}
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}
.photo {
  display: flex;
  margin-left: 5px;
  flex-direction: column;
  align-items: center;
}
</style>
