<template>
  <div class="card currency-container">
    <p class="title">Currency Converter</p>
    <div class="currency-box">
        <div class="amount">
            <label>Amount</label>
            <input class="form-control" type="text" v-model="amountBefore" @input="reset">
        </div>
        <div class="currency">
            <label>From</label>
            <select v-model="fromCurrency" @change="getCurrency" @click="reset">
                <option value="USD" selected>USD</option>
                <option value="MYR">MYR</option>
                <option value="EUR">EUR</option>
            </select>
        </div>
        <div class="currency">
            <label>To</label>
            <select v-model.lazy="toCurrency" @change="getCurrency" @click="reset">
                <option value="USD">USD</option>
                <option value="MYR">MYR</option>
                <option value="EUR" selected>EUR</option>
            </select>
        </div>
    </div>
    <button @click="convert">Convert</button>
    <div class="result"  v-if="result">
        <p>{{ amountBefore }} {{ fromCurrency }} = </p>
        <h4>{{ amountAfter }} {{ toCurrency }}</h4>
    </div>
    <div class="currency-details">
        1 {{ fromCurrency }} = {{ currency }} {{ toCurrency }} <br>
        1 {{ toCurrency }} = {{ 1/currency }} {{ fromCurrency }}
    </div>
  </div>
</template>

<script>
import axios from 'axios'
// import { mdiChevronRight } from '@mdi/js';
export default {
  data() {
      return {
          amountBefore: 0,
          amountAfter: 0,
          fromCurrency: 'USD',
          toCurrency: 'EUR',
          currency: '0.858885',
          result: false
          }
    },
  methods: {
        convert() {
            this.amountAfter = this.currency * this.amountBefore
            this.result = true
        },
        getCurrency() {
            let converter = `${this.fromCurrency}_${this.toCurrency}`
            axios.get(`https://free.currconv.com/api/v7/convert?q=${converter}&compact=ultra&apiKey=1172ef7ba1c07cc65d4d`)
            .then((res) => {
                this.currency = Object.values(res.data)[0]
            })
        },
        reset() {
            this.result = false
        }
    }   
}
</script>