<template>
  <div class="container">
    <!-- <Logo /> -->
    <div class="links">
      <h1 class="title">Users - {{this.all?'All users':'Recent activity'}}</h1>
      <div style="text-align:right;
                  margin: 0 1rem;
                  font-size: 1.2rem;">
        <label for="recent">Recent</label>
        <input v-on:click="checkRecent()" type="checkbox" id="recent" name="recent" :checked="true" />
        <!-- :checked="recent" -->
      </div>

      <ul>
        <li v-for="user in users" :key="user.id" class="news-item">
          <nuxt-link :to="'/users/'+user.id">
            <span class="host">{{ user.name }}, {{ user.city }}. {{ user.birdth }}</span>
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
      users: [],
      all: false,

      checkRecent() {
        this.all = !recent.checked;
        console.log("va", recent.checked);
        if (recent.checked) {
          axios
            .get("http://localhost:8080/backend/users/recent/10")
            .then((res) => (this.users = res.data.content));
        } else {
          axios
            .get("http://localhost:8080/backend/users")
            .then((res) => (this.users = res.data.content));
        }
      },
    };
  },
  mounted() {
    this.checkRecent();
  },
  /* async asyncData() {
    const { data } = await axios.get(
      "http://localhost:8080/backend/users/recent/10"
    );
    return { users: data.content };
  }, */
};
</script>

