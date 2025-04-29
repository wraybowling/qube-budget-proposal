<template>
  <div>
    <label for="amount">Amount:</label>
    <input
      type="number"
      id="amount"
      v-model="localSchedule.amount"
      step="0.01"
    />

    <label for="frequency">Frequency:</label>
    <select id="frequency" v-model="localSchedule.frequency">
      <option value="365">Daily</option>
      <option value="183">Every Two Days</option>
      <option value="52">Weekly</option>
      <option value="26">Every Two Weeks</option>
      <option value="12" default>Monthly</option>
      <option value="6">Every Two Months</option>
      <option value="4">Quarterly</option>
      <option value="2">Every Two Quarters</option>
      <option value="1">Yearly</option>
      <option value="0.5">Every Two Years</option>
    </select>
  </div>
</template>

<script>
export default {
  name: "QubeSchedule",
  props: {
    schedule: Object,
  },
  data() {
    return {
      localSchedule: { ...this.schedule },
    };
  },
  watch: {
    localSchedule: {
      deep: true,
      handler(schedule) {
        this.$emit("update:schedule", schedule);
      },
    },
  },
};
</script>

<style scoped>
/* Add your styles here */
</style>
