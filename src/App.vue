<template>
  <div id="app">
    <TextConverter />
    <CurrencyConverter />
  </div>
</template>

<script>
import TextConverter from './components/TextConverter.vue'
import CurrencyConverter from './components/CurrencyConverter.vue'
import './assets/App.css'

export default {
  name: 'App',
  components: {
    TextConverter,
    CurrencyConverter
  }
}
</script>
