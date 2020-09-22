<template>
  <div class=view>
    <Header />
    <div class="news-list">
      <Nuxt />
    </div>
  </div>
</template>
<script>
export default {
  layout: 'default'
}
</script>

<style lang="stylus">
.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 2em;
  color: #35495e;
  letter-spacing: 0.1em;
}

.subtitle {
  font-weight: 300;
  font-size: 1.6em;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

article 
  margin 4rem
  
.bloque
  margin 4rem

.news-item {
  background-color: #fff;
  border-bottom: 1px solid #eee;
  position: relative;
  line-height: 20px;

  .score {
    color: #ff6600;
    font-size: 1.1em;
    font-weight: 700;
    position: absolute;
    top: 50%;
    left: 0;
    width: 80px;
    text-align: center;
    margin-top: -10px;
  }

  .meta, .host {
    font-size: 0.85em;
    color: #828282;
  }

  a {
    display: inline-block;
    padding: 20px 30px 20px 80px;
    text-align: left;
    color: #222;
    width: 100%;
    height: 100%;
    text-decoration: none;

    &:hover {
      color: #ff6600;
    }
  }
}

.news-view {
  padding-top: 45px;
}

.news-list-nav, .news-list {
  background-color: #fff;
  border-radius: 2px;
}

.news-list-nav {
  padding: 15px 30px;
  position: fixed;
  text-align: center;
  top: 55px;
  left: 0;
  right: 0;
  z-index: 998;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);

  a {
    margin: 0 1em;
  }

  .disabled {
    color: #ccc;
  }
}



.slide-left-enter, .slide-right-leave-to {
  opacity: 0;
  transform: translate(30px, 0);
}

.slide-left-leave-to, .slide-right-enter {
  opacity: 0;
  transform: translate(-30px, 0);
}

.item-move, .item-enter-active, .item-leave-active {
  transition: all 0.5s cubic-bezier(0.55, 0, 0.1, 1);
}

.item-enter {
  opacity: 0;
  transform: translate(30px, 0);
}

.item-leave-active {
  position: absolute;
  opacity: 0;
  transform: translate(30px, 0);
}

@media (max-width: 600px) {
  .news-list {
    margin: 10px 0;
  }
}
</style>
