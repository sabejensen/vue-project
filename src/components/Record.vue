<template>
<div class="outer-wrapper">
<p>{{info.type}} - {{info.date}}</p>
  <div class="wrapper">
    <div>
    <p v-if="info.type != 'Running'">Reps</p>
    <p v-if="info.type == 'Running'">Distance (mi)</p>
    <p>{{info.val1}}</p>
    </div>
    <div>
    <p v-if="info.type != 'Running'">Sets</p>
    <p v-if="info.type == 'Running'">Time</p>
    <p>{{info.val2}}</p>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'Record',
  props: {
    info: Object
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
    height: 60px;
    padding: 10px 10px 90px 10px;
}
</style>
