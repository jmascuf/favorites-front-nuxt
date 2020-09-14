<template>
  <div class="container">
    <div>
      <!-- <Logo /> -->
      <h1 class="title">nuxtJs-guide-project</h1>
      <div class="links">
        <ul>
          <li v-for="user in users" :key="user.id" class="news-item">
              <!-- :to="{name: 'users-id', params: {id: user.id}}" -->
            <nuxt-link
              :to="'/users/'+user.id"
              class="button-grey"
            >
            <span class="host">

            {{ user.name }}
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
  layout: "blog",

  async asyncData () {
    const { data } = await axios.get('http://localhost:8080/backend/users')
    return { users: data.content }
  }

};
</script>

<style lang="stylus">
.news-item
  background-color #fff
  padding 20px 30px 20px 80px
  border-bottom 1px solid #eee
  position relative
  line-height 20px
  .score
    color #ff6600
    font-size 1.1em
    font-weight 700
    position absolute
    top 50%
    left 0
    width 80px
    text-align center
    margin-top -10px
  .meta, .host
    font-size .85em
    color #828282
    a
      color #828282
      text-decoration underline
      &:hover
        color #ff6600
</style>
