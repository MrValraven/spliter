<template>
  <section class="spliter">
    <h1>S P L I <br>T T E R</h1>
    <div class="container">
      <div class="calculator">
        <div class="bill">
          <label for="bill">Bill</label>
          <input type="text" name="bill" pattern="[0-9]" placeholder="0.00" v-model="bill" @change="getTotalAmount()">
        </div>
        <div class="tips">
          <label for="tip">Select Tip %</label>
          <div class="tipPercentage">
            <a class="tip" @click="tipPercentage = 5">5%</a>
            <a class="tip" @click="tipPercentage = 10">10%</a>
            <a class="tip" @click="tipPercentage = 15">15%</a>
            <a class="tip" @click="tipPercentage = 25">25%</a>
            <a class="tip" @click="tipPercentage = 50">50%</a>
            <input type="text" name="tip" pattern="[0-9]" placeholder="Custom" v-model="tipPercentage" @change="getTotalAmount()">
          </div>
        </div>
        <div class="people">
          <label for="people">Number of People</label>
          <input id="peopleInput" type="text" name="people" pattern="[0-9]" placeholder="0" v-model="numberOfPeople" @change="getTotalAmount()">
        </div>
      </div>
      <div class="total">
        <div class="amounts">
          <div class="tipAmount">
            <h3>Tip Amount<br><span>/ person</span></h3>
            <h2>${{(tipAmount / numberOfPeople).toFixed(2)}}</h2>
          </div>
          <div class="tipTotal">
            <h3>Total<br><span>/ person</span></h3>
            <h2>${{total.toFixed(2)}}</h2>
          </div>
        </div>
        <button @click="reset()">RESET</button>
      </div>
    </div>
    <div class="attribution">
      Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>. 
      Coded by <a href="#">Tiago Costa</a>.
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';


export default defineComponent({
  name: 'Home',
  data() {
    return {
      bill: 0,
      tipPercentage: 10,
      numberOfPeople: 2,
      tipAmount: 0,
      totalBill: 0,
      total: 0.00,
    }
  },
  methods: {
    getTotalAmount() {
      this.bill = Math.round(this.bill *100) / 100;
      this.tipAmount = (this.tipPercentage * 0.01 * this.bill);
      this.totalBill = this.bill + this.tipAmount
      this.total = this.totalBill / this.numberOfPeople;

    },
    reset() {
      this.bill = 0,
      this.tipPercentage = 10;
      this.numberOfPeople = 2;
      this.tipAmount = 0;
      this.totalBill = 0;
      this.total = 0.00;
    },
  }
  
});
</script>

<style lang="scss" scoped>

$strongCyan: hsl(172, 67%, 45%);
$darkCyan: hsl(183, 100%, 15%);
$greyishCyan: hsl(186, 14%, 43%);
$greyishCyan1: hsl(184, 14%, 56%);
$lightCyan: hsl(185, 41%, 84%);
$lightCyanNon: hsl(189, 41%, 97%);
$white: hsl(0, 0%, 100%);

.spliter {
  display: flex;
  height: 100vh;
  align-items: center;
  flex-direction: column;

  h1 {
    margin-top: 100px;
    margin-bottom: 70px;
  }
}

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: $white;
  width: 50%;
  padding: 20px;
  border-radius: 25px;
   box-shadow: 0px 3px 15px $greyishCyan1;


  .calculator {
    width: 60%;
    height: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-direction: column;
    padding: 20px;

    .bill,
    .people {
      display: flex;
      align-items: flex-start;
      flex-direction: column;
      width: 100%;
      margin-top: 15px;

      label {
        color: $greyishCyan;
        font-weight: 700;
      }

      input {
        width: 80%;
        padding: 5px 5px 5px 10px;
        margin-bottom: 15px;
        border-radius: 5px;
        border: none;
        outline: none;
        background-color: $lightCyan;
        font-family: 'Space mono', monospace;
        font-weight: 700;
        font-size: 24px;
        text-align: right;
        background: url(../assets/icon-dollar.svg) no-repeat scroll 15px 15px;
        background-color: $lightCyanNon;

        &:focus-within {
          border: 1px solid $strongCyan;
        }
      }

      #peopleInput {
        margin-top: 0;
        background: url(../assets/icon-person.svg) no-repeat scroll 15px 15px;
        background-color: $lightCyanNon;
      }
    }

    .tips {
      display: flex;
      align-items: flex-start;
      flex-direction: column;

      label {
        color: $greyishCyan;
        font-weight: 700;
      }

      .tipPercentage {
        display: flex;
        flex-wrap: wrap;
        flex: 0 0 30%;

        a {
          color: $lightCyanNon;
          background-color: $darkCyan;
          padding: 10px 20px 10px 20px;
          border-radius: 6px;
          margin: 10px 10px 10px 0;
          width: 50px;
          cursor: pointer;
          transition: all 0.5s cubic-bezier(0.075, 0.82, 0.165, 1);

          &:hover {
            background-color: $lightCyan;
            color: $darkCyan;
          }
          &:active {
            background-color: $strongCyan;
            color: $darkCyan;
          }
        }

        .selectedTip {
          background-color: $strongCyan;
        }

        input {
          width: 50px;
          padding: 10px 20px 10px 20px;
          border-radius: 6px;
          outline: none;
          border: none;
          margin: 10px 10px 10px 0;
          font-family: 'Space mono', monospace;
          font-weight: 700;
          font-size: 14px;
          text-align: right;
          background-color: $lightCyanNon;

          &:focus-within {
            border: 1px solid $strongCyan;
          }

          &::-webkit-input-placeholder { /* Chrome/Opera/Safari */
            text-align: center;
            color: $darkCyan;
          }
          &::-moz-placeholder { /* Firefox 19+ */
            text-align: center;
            color: $darkCyan;
          }
          &:-ms-input-placeholder { /* IE 10+ */
            text-align: center;
            color: $darkCyan;
          }
          &:-moz-placeholder { /* Firefox 18- */
            text-align: center;
            color: $darkCyan;
          }
        }
      }
    }

  }

  .total {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    width: 40%;
    height: 80%;
    background-color: $darkCyan;
    padding: 20px 30px 20px 30px;
    border-radius: 12px;

    .amounts {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: flex-start;
      width: 100%;
    }

    .tipAmount,
    .tipTotal {
      display: flex;
      justify-content: space-between;
      align-items: center;
      width: 100%;
    }

    h2 {
      color: $strongCyan;
      font-size: 35px;
    }

    h3 {
      color: $lightCyanNon;
      text-align: left;
      font-size: 16px;
    }
    span {
      color: $greyishCyan;
    }

    button {
      border: none;
      background-color: $strongCyan;
      color: $darkCyan;
      padding: 10px 5px 10px 5px;
      width: 90%;
      border-radius: 6px;
      cursor: pointer;
      font-weight: 700;
      transition: all 0.5s cubic-bezier(0.075, 0.82, 0.165, 1);

      &:hover {
        background-color: $lightCyan;
      }
    }
  }
}

.attribution {
  position: absolute;
  bottom: 20px;
  color: $darkCyan;

  a {
    color: $darkCyan;
  }
}


</style>
