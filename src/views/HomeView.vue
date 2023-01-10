<!-- eslint-disable vue/no-unused-vars -->
<!-- eslint-disable vue/require-v-for-key -->
<template>
  <div class="home">
    <div class="container">
      <CardComponent @likeMars="likeMars"/>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import CardComponent from "@/components/CardComponent.vue";

export default {
  name: "HomeView",
  components: {
    CardComponent,
  },
  methods : {
    likeMars : function (){
      return alert("You like mars ? Me too");
    }
  }
};
</script>
