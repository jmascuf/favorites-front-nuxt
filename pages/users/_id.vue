<template>
  <div class="container">
    <article>
      <h1 class="title">{{name}}</h1>
      <p>{{birdth}}</p>
      <p>{{city}}</p>
      <p>{{eMail}}</p>
      <router-link :to="`/assessments/user/${id}`">Assessments</router-link>
        
    </article>

  </div>

</template>


<script>
import axios from "axios";

export default {
  layout: "detail",


  validate({ params }) {
    return !isNaN(+params.id);
  },
  async asyncData({ params, error }) {
    
    try {
      const { data } = await axios.get(
        `http://localhost:8080/backend/users/${+params.id}`
      );
      return data;
    } catch (e) {
      error({ message: "User not found", statusCode: 404 });
    }

    
  },
};
</script>

