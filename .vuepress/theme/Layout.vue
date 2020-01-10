
<template>
  <div class="theme-container" >
<component class="main-content" :is="layout"></component>
  </div>
</template>

<style lang="stylus">
@import url('https://fonts.googleapis.com/css?family=Source+Sans+Pro:300,400,700&display=swa');
html, body
  padding 0
  margin 0
  background-color #f4f8fb
  -ms-text-size-adjust 100%
  -webkit-text-size-adjust 100%
body
  font-family "Source Sans Pro",Helvetica,sans-serif
  font-size 16px
  text-rendering optimizeLegibility
  -webkit-font-smoothing antialiased
strong
  font-weight 600
h1, h2, h3, h4, h5, h6
  font-weight 600
  line-height 1.25
  font-family "Source Sans Pro",Helvetica,sans-serif
a
  color: #7EBDC2
p, ul, ol
  line-height 1.7
</style>

<script>
 import Home from './layouts/Home.vue'
 import StudentLoans from './layouts/StudentLoans.vue'
 import HowMuchHouseCanIAfford from './layouts/HowMuchHouseCanIAfford.vue'
 import StockDistribution from './layouts/stockDistribution.vue'
 export default{
     components: {Home,StudentLoans, HowMuchHouseCanIAfford, StockDistribution},
     computed: {
         layout(){
             const{path} = this.$page
             console.log(path)
             if(path === "/"){
                 return 'Home'
             }else if(path === "/student_loans.html"){
                 return 'StudentLoans'
             }else if(path == '/how-much-house-can-i-afford.html'){
                 return 'how-much-house-can-i-afford'
             }else if(path == '/stock-distribution.html'){
                 return 'StockDistribution'
             }
         }
     }
 }
</script>
