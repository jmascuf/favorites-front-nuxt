<template>
  <div class="container">
    <div>
      <h1 class="title">Books</h1>
      <RegistriesList v-if="registries" :registries="registries" />
    </div>
  </div>
</template>


<script>
import axios from "axios";

export default {
  layout: "list",
  validate({ params }) {
    let val = false;
    params.media =='book'?val = true: val = false;
    return val;
  },
  async asyncData({ params, error }) {
    const { data } = await axios.get(
      `http://localhost:8080/backend/registries/topFavorite/${params.media}`
      
    );
    console.log('se da ', params.media)
    return { registries: data.content };
  },
};
</script>

