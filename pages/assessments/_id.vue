<template>
  <div class="container">
    <article>
      <h1 class="title">{{user.name}} about {{registry.title}}</h1>
      <p>{{favorite}}</p>
      <p>{{recommend}}</p>
      <p>{{notes}}</p>
      <nuxt-link :to="`/registries/${registry.id}`">
              <span class="host">
                <p >{{registry.title}}</p>
              </span>
            </nuxt-link>
  
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
        `http://localhost:8080/backend/assessments/${+params.id}`
      );
      return data;
    } catch (e) {
      error({ message: "User not found", statusCode: 404 });
    }

    
  },
};
</script>

