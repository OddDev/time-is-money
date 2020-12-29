<template>
  <div id="app">
    <h1>Time is Money</h1>
    <p>
      This is a list of dates. They are calculated by substracting a certain
      amount of seconds from the current date. This aids as a reminder how
      absurdetily high the net worth of some human-beings is.
    </p>
    <money-time />
  </div>
</template>

<script>
import MoneyTime from "./components/MoneyTime.vue";

export default {
  name: "App",
  components: {
    MoneyTime,
  },
};
</script>
MoneyTime

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 3em 2em 0 2em;
  display: flex;
  flex-direction: column;
  money-time {
    flex-grow: 1;
  }
}
body {
  margin: 0;
}
</style>
