<template>
  <div class="card text-container">
    <p class="title">Lowercase Converter</p>
    <input class="form-control" type="text" v-model="msg" placeholder="Fill in some text with lower and upper case">
    <div class="text-box">
      <h1>{{ msg.toLowerCase() }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  data() {
      return {
          msg: ''
          }
    }  
}
</script>


