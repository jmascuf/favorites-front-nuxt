<template>
  <div class="container">
    <div class=links>
      <h1 class="title">Registries</h1>
      <RegistriesList v-if="registries" :registries=registries />
    </div> 
  </div>
</template>


<script>
import axios from "axios";

export default {
  layout: "list",

   async asyncData() {
    const { data } = await axios.get(
      "http://localhost:8080/backend/registries"
    );
    return { registries: data.content };
  }, 
};
</script>

