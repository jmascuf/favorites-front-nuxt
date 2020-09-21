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
        <AssessmentsList :assessments="assessments" media="book" />
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
    };
  },

  async fetch() {
    
    await axios
      .get(`http://localhost:8080/backend/users/${+this.$route.params.id}`)
      .then((res) => (this.user = res.data));

    await axios
      .get(`http://localhost:8080/backend/assessments/user/${+this.$route.params.id}`)
      .then((res) => (this.assessments = res.data.content));
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

