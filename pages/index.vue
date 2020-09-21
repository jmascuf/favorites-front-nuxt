<template>
  <div class="container">
    <p v-if="$fetchState.pending">Fetching posts...</p>
    <p v-else-if="$fetchState.error">Error while fetching posts: {{ $fetchState.error.message }}</p>
    <div v-else class=links>
      <div class="bloque">
        <h2 class="title">Books - Top favorites</h2>
        <RegistriesList :registries="books" media="book" />
      </div>
      <div class="bloque">
        <h2 class="title">Films - Top favorites</h2>
        <RegistriesList :registries="films" media="film" />
      </div>
      <div class="bloque">
        <h2 class="title">Series - Top favorites</h2>
        <RegistriesList :registries="series" media="book" />
      </div>
      <div class="bloque">
        <h2 class="title">Albums - Top favorites</h2>
        <RegistriesList :registries="albums" media="film" />
      </div>
    </div>

    <!-- <router-link to="/topFavorite/book">top books</router-link> -->
  </div>
</template>

<script>
import axios from "axios";

export default {
  layout: "list",


  data() {
    return {
      books: [],
      films: [],
      series: [],
      albums: [],
    };
  },

  async fetch() {
    await axios
      .get("http://localhost:8080/backend/registries/topFavorite/book")
      .then((res) => (this.books = res.data.content));

    await axios
      .get("http://localhost:8080/backend/registries/topFavorite/film")
      .then((res) => (this.films = res.data.content));

    await axios
      .get("http://localhost:8080/backend/registries/topFavorite/serie")
      .then((res) => (this.series = res.data.content));
    
    await axios
      .get("http://localhost:8080/backend/registries/topFavorite/album")
      .then((res) => (this.albums = res.data.content));
  },

  fetchOnServer: false,


/**
  async asyncData({ error }) {
    const { data } = await axios.get(
      `http://localhost:8080/backend/registries/topFavorite/book`
      
    );
    
    return { books: data.content };
    
  },
*/


};

</script>
