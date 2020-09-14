<template>
  <div class="container">
    <article>
      <h1 class="title">{{name}}</h1>
      <p>{{birdth}}</p>
      <p>{{city}}</p>
      <p>{{eMail}}</p>
    </article>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  layout: "blog",


  validate ({ params }) {
    return !isNaN(+params.id)
  },
  async asyncData ({ params, error }) {
    try {
      const { data } = await axios.get(`http://localhost:8080/backend/users/${+params.id}`)
      
      return data
    } catch (e) {
      error({ message: 'User not found', statusCode: 404 })
    }
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