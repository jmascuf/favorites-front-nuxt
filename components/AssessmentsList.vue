<template>
    <!-- <div>
    </div> -->
      <div class="links" v-if="assessments">
        <ul>
          <li v-for="assessment in assessments" :key="assessment.id" class="news-item">
            
            <nuxt-link :to="'/assessments/'+assessment.id">
              <span
                class="host"
              >{{ assessment.registry.title }}, {{ assessment.registry.author }}. {{ assessment.registry.productionDate[0] }}</span>
            </nuxt-link>
            <span>{{assessment.favorite}}</span>
            <span>{{assessment.recommed}}</span>
            <span>{{assessment.notes}}</span>
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
    media: String
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