<template>
  <div class="container">
    <div>
      <!-- <Logo /> -->
      <h1 class="title">nuxtJs-guide-project</h1>
      <div class="links">
        <ul>
          <li v-for="user in users" :key="user.id" class="news-item">
            <nuxt-link :to="'/users/'+user.id">
              <span class="host">
              {{ user.name }}, {{ user.city }}. {{ user.birdth }}
              </span>
            </nuxt-link>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>


<script>
import axios from 'axios'

export default {
  layout: "list",

  async asyncData () {
    const { data } = await axios.get('http://localhost:8080/backend/users/recent/10')
    return { users: data.content }
  }

};
</script>

