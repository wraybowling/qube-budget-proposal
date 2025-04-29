<template>
  <QubeSchedule
    v-for="(schedule, index) in schedules"
    :key="index"
    :schedule="schedule"
    @update:schedule="updateSchedule(index, $event)"
  />
  <button @click="addSchedule">Add Schedule</button>
  <p>Budget: {{ sum }}</p>
</template>

<script>
import QubeSchedule from "./components/QubeSchedule.vue";

export default {
  name: "App",
  components: {
    QubeSchedule,
  },
  data() {
    return {
      schedules: [{ amount: 0, frequency: 12 }],
    };
  },
  methods: {
    addSchedule() {
      this.schedules.push({ amount: 0, frequency: 12 });
    },
    updateSchedule(index, schedule) {
      this.schedules[index] = schedule;
    },
  },
  computed: {
    sum() {
      return this.schedules.reduce(
        (acc, schedule) => acc + (schedule.amount * schedule.frequency) / 12,
        0
      );
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
