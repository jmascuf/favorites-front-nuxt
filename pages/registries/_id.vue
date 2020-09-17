<template>
  <div class="container">
    <article>
      <h1 class="title">{{title}}</h1>
      <p>{{media}}</p>
      <p>{{author}}</p>
      <p>{{productionDate}}</p>
 
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
        `http://localhost:8080/backend/registries/${+params.id}`
      );
      return data;
    } catch (e) {
      error({ message: "User not found", statusCode: 404 });
    }

    
  },
};
</script>

