<template>
  <div class="container">
    <article>
      <div class="links">
        <ul>
          <li v-for="item in content" :key="item.id" class="news-item">
            <nuxt-link :to="`/registry/${item.registry.id}`">
              <span class="host">
                <p >{{item.registry.title}}</p>
              </span>
            </nuxt-link>
          </li>
        </ul>
      </div>
      <!-- <p>{{title}}</p>
      <p>{{author}}</p>
      <p>{{media}}</p>-->
      <!-- <router-link :to="`/assessments/${retgistry.id}`">Registry</router-link> -->
    </article>
    <!-- <lista :list='assessments' entity='assessments'>
    </lista>-->
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
        `http://localhost:8080/backend/assessments/user/${+params.id}`
      );
      console.log(data);
      return data;
    } catch (e) {
      error({ message: "User not found", statusCode: 404 });
    }
  },
};
</script>
