<template>
  <div class="container">
    <div>
      <!-- <Logo /> -->
      <h1 class="title">
        nuxtJs-guide-project
      </h1>
      <div class="links">
        <!-- <nuxt-link
          v-for="user in users" 
          :to="{name: 'user-id', params: {id: user.id}}"
          :key="user.id"
          class= "button-grey"
          >
          {{user.titles}}
        </nuxt-link> -->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  layout: 'blog',
  /* components: {
    Logo
  }, */
/*
  data(){
    user=[];
  },
   computed: {
    users () {
      return this.$store.state.all
    } 
  },
  created() {
    axios
      .get('http://localhost:8080/backend/users/')
      .then(response => this.users=response.content)
      .catch(err => console.log(err));
  } */
  

}
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
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
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
