<template>
<div class="calculator">
  <a href="/" class="nav-item">Home</a>
  <div class="houseAfordibility">
    <h2>So You have some money to invest in this months SA picks? how do you split it?</h2>

    <h4>This months picks are:</h4>
    <ul>
      <li v-for="stock in stocks">
        <strong>{{stock.name}}</strong> ({{stock.ticker}}) - {{stock.price}}
      </li>
    </ul>

    <h4>How much do you have to invest?</h4>
    <input name="Money" type="text" placeholder="1000? 2000? or what ever" v-model="amountToInvest" />

    <h4>Does your brokerage allow you to do partial shares?</h4>
    <div class="check-container">
      <input type="checkbox" name="partial-shares" value="partial-shares" v-model="fractionalShares">
      <span>my brokerage allows partial shares</span>
    </div>
    <div v-if="showResults">

      <p>you should buy:</p>
      <ul>
        <li v-for="stock in stocks">
          <strong>{{stock.name}}</strong> ({{stock.ticker}}) - {{stock.tobuy}} shares
        </li>
      </ul>


      </p>
    </div>

  </div>
</div>
</template>



<style lang="scss">
 input{
     width: calc(100% - 20px);
 }
 .calculator{
     width: 100%;
     margin: 10px
 }
 .check-container{
   display:flex;
   justify-content: flex-start;
   & > input {
     width: auto;
   }
 }
 .result{
     font-size:25px;
 }
 button{
     background: #3075ff;
     border-radius: 10px;
     border: none;
     color: white;
     font-size: 19px;
     text-transform: uppercase;
     padding: 10px;
 }

</style>


<script>

export default{
  computed: {
    showResults(){
      this.investmentBreakdown = ""
      const amountToInvest = this.amountToInvest
      if(parseFloat(this.amountToInvest)< 100){return false}


      let amountPerStock = parseFloat(this.amountToInvest)/parseFloat(this.stocks.length)

      if(this.fractionalShares){
        this.stocks.map(stonk => {
          stonk.tobuy =  amountPerStock / stonk.price

        })
      }else{
        let investableAmount = amountToInvest
        this.stocks.map(stonk => {
          if(amountPerStock > stonk.price){
            stonk.tobuy = Math.floor(parseFloat(amountPerStock) / parseFloat(stonk.price));
          }
          // investableAmount = investableAmount - (stonk.tobuy * stong.price)
          // amountPerStock = investableAmount
        })
      }

      return true
    },
    costOfHousing(){

      return 1
    },
    loanSize(){
      let studentLoan = parseFloat(this.downpayment).toFixed(2)
      if(studentLoan){
        return parseFloat(parseFloat(this.costOfHousing).toFixed(2) - parseFloat(this.downpayment).toFixed(2))
      }else{
        /* todo: add "come on, where is your downpayment" */
        return parseFloat(this.costOfHousing).toFixed(2)
      }
    }
  },
  data(){
    return {
      amountToInvest: "0",
      investmentBreakdown: "",
      fractionalShares: false,
      stocks: [
        {
          "ticker": "nsdaq:1",
          "name": "stock 1",
          "price": 123,
          "tobuy": 0
        },
        {
          "ticker": "nsdaq:2",
          "name": "stock 2",
          "price": 5555,
          "tobuy": 0
        },
        {
          "ticker": "nsdaq:3",
          "name": "stock 3",
          "price": 23.25,
          "tobuy": 0
        },
        {
          "ticker": "nsdaq:4",
          "name": "stock 4",
          "price": 245,
          "tobuy": 0
        }
      ]
    }

  },
}

</script>
