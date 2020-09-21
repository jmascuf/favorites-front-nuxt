<template>
  <div class="container">
    <p v-if="$fetchState.pending">Fetching posts...</p>
    <p v-else-if="$fetchState.error">Error while fetching posts: {{ $fetchState.error.message }}</p>
    <div v-else class=links>
      <article>
        <h1 class="title">{{user.name}}</h1>
        <p>{{user.birdth}}</p>
        <p>{{user.city}}</p>
        <p>{{user.eMail}}</p>
        <!-- <router-link :to="`/assessments/user/${user.id}`">Assessments</router-link> -->
      </article>
      <div class="bloque">
        <h2 class="title">Favorites</h2>
     
        <AssessmentsList :assessments="books" v-if=books media="books" categ="fav" />
        <AssessmentsList :assessments="films" v-if=films media="films" categ="fav" />
        <AssessmentsList :assessments="albums" v-if=albums media="albums" categ="fav" />
        <AssessmentsList :assessments="comics" v-if=comics media="comics" categ="fav" />
        <AssessmentsList :assessments="series" v-if=series media="series" categ="fav" />

        <h2 class="title">Recommended</h2>
        <AssessmentsList :assessments="books" v-if=books media="books" categ="req" />
        <AssessmentsList :assessments="films" v-if=films media="films" categ="req" />
        <AssessmentsList :assessments="albums" v-if=albums media="albums" categ="req" />
        <AssessmentsList :assessments="comics" v-if=comics media="comics" categ="req" />
        <AssessmentsList :assessments="series" v-if=series media="series" categ="req" />
      </div>
    </div>
  </div>
</template>


<script>
import axios from "axios";

export default {
  layout: "list",
  id: String,
  validate({ params }) {
    this.id=params.id;
    return !isNaN(+params.id);
    
  },

  data() {
    return {
      user: {},
      assessments: [],
      books: [],
      films: [],
      albums: [],
      comics: [],
      series: [],
    };
  },

  async fetch() {
    
    await axios
      .get(`http://localhost:8080/backend/users/${+this.$route.params.id}`)
      .then((res) => (this.user = res.data));

    await axios
      .get(`http://localhost:8080/backend/assessments/user/${+this.$route.params.id}/book`)
      .then((res) => (this.books = res.data.content));
    await axios
      .get(`http://localhost:8080/backend/assessments/user/${+this.$route.params.id}/film`)
      .then((res) => (this.films = res.data.content));
    await axios
      .get(`http://localhost:8080/backend/assessments/user/${+this.$route.params.id}/album`)
      .then((res) => (this.albums = res.data.content));
    await axios
      .get(`http://localhost:8080/backend/assessments/user/${+this.$route.params.id}/comic`)
      .then((res) => (this.comics = res.data.content));
    await axios
      .get(`http://localhost:8080/backend/assessments/user/${+this.$route.params.id}/serie`)
      .then((res) => (this.series = res.data.content));
  },

  fetchOnServer: false,

  /*  async asyncData({ params, error }) {
   
      await axios.get(`http://localhost:8080/backend/users/${+params.id}`)
      .then((res) => console.log(data.user, res.data));

      await axios.get(`http://localhost:8080/backend/assessments/user/${+params.id}`)
      .then((res) => console.log(res.data.content)); 
  },*/ 
};
</script>

