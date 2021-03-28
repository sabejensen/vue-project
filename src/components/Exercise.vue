<template>
<div class="outer-wrapper">
  <div class="wrapper">
    <div>
    <p>{{param[0]}}</p>
    <input v-model="amount.a" placeholder="0" type="number">
    </div>
    <div>
    <p>{{param[1]}}</p>
    <input v-if="param[1] != 'Time'" v-model="amount.b" placeholder="0" type="number" >
    <input v-if="param[1] == 'Time'" class="time" v-model="amount.b" >
    </div>
  </div>
  <button v-on:click="onButton">Add</button>
</div>
</template>

<script>
export default {
  name: 'Exercise',
  props: {
    param: Array
  },
  methods: {
    onButton () {
        this.$emit('added', this.amount)
    }
  },
  data: () => {
    return {
      amount: {
          a: '',
          b: ''
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.wrapper {
    display: flex;
    justify-content: space-around;
}
.outer-wrapper {
    background-color: #eee;
    width: 40%;
    margin: auto;
    height: 90px;
    padding: 10px 10px 70px 10px;
}
input {
    width: 60px;
    height: 35px;
    border-radius: 15px;
    font-size: 14pt;
}
.time {
    width: 80px;
}
button {
    width: 70px;
    height: 30px;
    border: none;
    border-radius: 30px;
    background-color: #4c49f5;
    color: #fff;
    margin-bottom: 10px;
}
button:hover {
    background-color: #6c6aff;
}
</style>
