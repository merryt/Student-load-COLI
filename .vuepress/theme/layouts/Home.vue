<template>
  <div class="calculator">
    <h1>Home</h1>
    <a href="/student_loans.html" class="nav-item">Where can you live with those student loans</a> <br/>
    <a href="/how-much-house-can-i-afford.html" class="nav-item">How much house can I afford?</a> <br/>
    <a href="/stock-distribution.html" class="nav-item">I have x to invest on this months stock picks, how should I split it?</a>
  </div>
</template>



<style>
 input{
     width: calc(100% - 20px);

 }
 .calculator{
     width: 100%;
     margin: 10px
 }
 .result{
     font-size:50px;
 }
</style>


<script>

export default{
     data(){
         return {
             downpayment: 0
         }

    },
 }
</script>
