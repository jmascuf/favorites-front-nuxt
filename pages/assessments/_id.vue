<template>
  <div class="container">
    <article>
      <h1 class="title">{{user.name}} <span style="font-size:.5em">from</span> {{user.city}} ({{user.year || '----'}})</h1>
      <h1 class="subtitle">about</h1>
        <nuxt-link :to="`/registries/${registry.id}`">
      <h1 class="subtitle">{{registry.title}} 
      <!--   <span class="host" style="font-size:.5em; text-decoration:underline">
            search
        </span> -->
      </h1>
      </nuxt-link>
      <p class="punctuation">

      <span>Favorite score: {{favorite}}</span>
      <span>Recommend score: {{recommend}}</span>
      </p>
      

      <div class=notas>{{notes}}</div>
    </article>
  </div>
</template>


<script>
import axios from "axios";

export default {
  layout: "item-detail",

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

<style lang="stylus" scoped>
.notas{
  padding: 2em 2em 4em 2em;
background: white;
width: 100%;
}
.punctuation{
  padding: 0em 0em 2em 0em;
}
</style>

