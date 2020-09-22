<template>
  <div class="container">
    <p v-if="$fetchState.pending">Fetching posts...</p>
    <p v-else-if="$fetchState.error">Error while fetching posts: {{ $fetchState.error.message }}</p>
    <div v-else class="links">
      <article>
        <h1 class="title">{{registry.title}}</h1>
        <p>{{registry.media}}</p>
        <p>{{registry.author}}</p>
        <p>{{registry.productionDate}}</p>
      
      <a
        :href="`https://www.google.com/search?q=${registry.title}, ${registry.author}, ${registry.productionDate[0]}`"
        target="_blank"
        rel="search"
        referrerpolicy
      >search in Google</a>
      -
      <a
        :href="`https://www.bing.com/search?q=${registry.title}, ${registry.author}, ${registry.productionDate[0]}`"
        target="_blank"
        rel="search"
        referrerpolicy
      >search in Bing</a>
      </article>
      <h2>Assessments</h2>
      

      <ul>
          <li v-for="assessment in assessments" :key="assessment.id" class="news-item">
            
            <nuxt-link :to="'/assessments/'+assessment.id" 
            >
            <!-- v-if="(categ=='req' && assessment.recommend!=0) || (categ=='fav' && assessment.favorite!=0)  " -->
            <span
                class="host"
              >{{ assessment.user.name }}, {{ assessment.user.city }}.</span>
            <span class="pull-right notes" title="Notes" >{{assessment.notes}}</span>
            <span class="pull-right" title="Recommend" >{{assessment.recommend}}</span>
            <span class="pull-right" title="Favorite" >{{assessment.favorite}}</span>
            </nuxt-link>
          </li>
        </ul>



    </div>
  </div>
</template>


<script>
import axios from "axios";

export default {
  layout: "list",

  data() {
    return {
      registry: null,
      assessments: [],
    };
  },

  validate({ params }) {
    return !isNaN(+params.id);
  },

  async fetch() {
    try {
      await axios
        .get(
          `http://localhost:8080/backend/registries/${+this.$route.params.id}`
        )
        .then((res) => (this.registry = res.data));
    } catch (e) {
      error({ message: "Registry not found", statusCode: 404 });
    };
    try {
      await axios
        .get(
          `http://localhost:8080/backend/assessments/registry/${+this.$route.params.id}`
        )
        .then((res) => (this.assessments = res.data.content));
    } catch (e) {
      error({ message: "Assessments not found", statusCode: 404 });
    }
  },
};
</script>

