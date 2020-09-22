<template>
     <div class="links" v-if="assessments">
       <h3 class="subtitle">{{media}}</h3>
        <ul>
          <li v-for="assessment in assessments" :key="assessment.id" class="news-item">
            
            <nuxt-link :to="'/assessments/'+assessment.id" 
            v-if="(categ=='req' && assessment.recommend!=0) || (categ=='fav' && assessment.favorite!=0)  "
            >
              <span
                class="host"
              >{{ assessment.registry.title }}, {{ assessment.registry.author }}. {{ assessment.registry.productionDate[0] }}</span>
            <span class="pull-right notes" title="Notes" >{{assessment.notes}}</span>
            <span class="pull-right" title="Recommend" >{{assessment.recommend}}</span>
            <span class="pull-right" title="Favorite" >{{assessment.favorite}}</span>
            </nuxt-link>
          </li>
        </ul>
      </div>
  <!-- <div class="container">
  </div> -->
</template>
<script>
export default {
  props: {
    assessments: Array,
    media: String,
    categ: String,
  },

};
</script>

 <!--
/* 
id	863
user	
id	42
    name	"Joana"
    eMail	"joana@barcelona.exp"
    city	"Barcelona"
    birdth	null
registry	
    id	57
    title	"1984"
    productionDate	
    0	1949
    1	1
    2	1
    media	"book"
    author	"George Orwell"
    registeredAt	
    0	2020
    1	6
    2	26
    3	16
    4	33
    5	55
favorite	9
recommend	6
notes	"Great!"
links	
0	
rel	"self"
href	"http://localhost:8080/backend/assessments/863"
1	
rel	"assessments"
href	"http://localhost:8080/backend/assessments/user/42"
 */
 -->

 <style lang="stylus" scoped>
 
 </style>