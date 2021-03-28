<template>
  <div class="hello">
    <h1>Exercise Tracker</h1>
    <select v-model="selected">
      <option disabled value="">Select a Workout</option>
      <option>Running</option>
      <option>Push-ups</option>
      <option>Benchpress</option>
    </select>
    <div class="header">
      <p>Selected: {{ selected }}</p>
    </div>
    <Exercise :param="paramSelect()" v-if="selected !== ''" v-on:added="addWork"/>
    <br>
    <h2 v-if="workouts.length > 0">Workout History</h2>
    <div v-for="workout in workouts" v-bind:key="workout.id" >
      <Record :info="workout" />
      <br>
    </div>
  </div>
</template>

<script>
import Exercise from './Exercise.vue'
import Record from './Record.vue'

export default {
  name: 'ExerciseList',
  props: {
    msg: String
  },
  components: {
    Exercise,
    Record
  },
  methods: {
    paramSelect: function () {
      let results = []
      if(this.selected == 'Benchpress') {
        results.push('Reps')
        results.push('Sets')
        return(results)
      } else if(this.selected == 'Push-ups') {
        results.push('Reps')
        results.push('Sets')
        return(results)
      } else {
        results.push('Distance (mi)')
        results.push('Time')
        return(results)
      }
    },
    addWork (value) {
      let now = new Date
      now = now.toDateString()
      let myObject = {
        date: now,
        type: this.selected,
        val1: value.a,
        val2: value.b,
        id: this.count
      }
      this.count += 1
      this.workouts.push(myObject)
    }
  },
  data: () => {
    return {
      selected: '',
      count: 0,
      workouts: []
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  font-size: 40pt;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
select {
  width: 30%;
  height: 40px;
  font-size: 16pt;
  border-radius: 10px;
}
.header {
  margin: auto;
}
</style>
