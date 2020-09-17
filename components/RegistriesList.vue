<template>
  <div class="container">
    <div>
      <div class="links" v-if="registries">
        <ul>
          <li v-for="registry in registries" :key="registry.id" class="news-item">
            <nuxt-link :to="'/registries/'+registry.id">
              <span
                class="host"
              >{{ registry.title }}, {{ registry.author }}. {{ registry.productionDate }}</span>
            </nuxt-link>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    registries: Array,
    media: String
  },
  /* async asyncData({ error }) {
    const { data } = await axios.get(
      `http://localhost:8080/backend/registries/topFavorite/film`
      
    );
    
    return { registries: data.content };
  },  */
};
</script>

