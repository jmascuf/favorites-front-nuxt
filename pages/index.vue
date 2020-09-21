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

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  width:100%;
}
</style>

<style lang="stylus">
body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Fira Sans', 'Droid Sans', 'Helvetica Neue', sans-serif;
  font-size: 15px;
  background-color: lighten(#eceef1, 30%);
  margin: 0;
  padding-top: 55px;
  color: #34495e;
  overflow-y: scroll;
}

a {
  color: #34495e;
  text-decoration: none;
}

.header {
  background-color: #ff6600;
  position: fixed;
  z-index: 999;
  height: 55px;
  top: 0;
  left: 0;
  right: 0;

  .inner {
    max-width: 800px;
    box-sizing: border-box;
    margin: 0px auto;
    padding: 15px 5px;
  }

  a {
    color: rgba(255, 255, 255, 0.8);
    line-height: 24px;
    transition: color 0.15s ease;
    display: inline-block;
    vertical-align: middle;
    font-weight: 300;
    letter-spacing: 0.075em;
    margin-right: 1.8em;

    &:hover {
      color: #fff;
    }

    &.router-link-active {
      color: #fff;
      font-weight: 400;
    }

    &:nth-child(6) {
      margin-right: 0;
    }
  }

  .github {
    color: #fff;
    font-size: 0.9em;
    margin: 0;
    float: right;
  }
}

.logo {
  width: 24px;
  margin-right: 10px;
  display: inline-block;
  vertical-align: middle;
}

.view {
  max-width: 800px;
  margin: 0 auto;
  position: relative;
}

.fade-enter-active, .fade-leave-active {
  transition: all 0.2s ease;
}

.fade-enter, .fade-leave-active {
  opacity: 0;
}

.bloque {
  margin: 5em 0;
}

@media (max-width: 860px) {
  .header .inner {
    padding: 15px 30px;
  }
}

@media (max-width: 600px) {
  .header {
    .inner {
      padding: 15px;
    }

    a {
      margin-right: 1em;
    }

    .github {
      display: none;
    }
  }
}


</style>