<template>
  <div class="container">
    <div>
      <!-- <Logo /> -->
      <h1 class="title">nuxtJs-guide-project</h1>
      <div class="links">
        <ul>
          <li v-for="user in users" :key="user.id">
              <!-- :to="{name: 'users-id', params: {id: user.id}}" -->
            <nuxt-link
              :to="'/users/'+user.id"
              class="button-grey"
            >{{ user.name }}</nuxt-link>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  layout: "blog",

  async asyncData () {
    const { data } = await axios.get('http://localhost:8080/backend/users')
    return { users: data.content }
  }

};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
