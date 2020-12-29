<template>
  <div class="money-time">
    <div class="money-time-navigation">
      <a
        class="money-time-navigation__entry"
        :href="'#' + range.value"
        :key="range.value"
        v-for="range in ranges"
      />
    </div>
    <ul class="money-time-list">
      <li :id="range.value" :key="range.value" v-for="range in ranges">
        <date-list-item :value="range.value" :name="range.name" />
      </li>
    </ul>
  </div>
</template>

<script>
import DateListItem from "./DateListItem.vue";
import axios from "axios";
export default {
  components: { DateListItem },
  name: "MoneyTime",
  data() {
    return {
      ranges: [
        { value: 10000, name: "ten-thousand" },
        { value: 1000000, name: "million" },
        { value: 70000000, name: "Giannis Antetokounmpo" },
        { value: 100000000, name: "one-hundred million" },
        { value: 1000000000, name: "billion" },
        { value: 1800000000, name: "GPP of Greenland" }
      ]
    };
  },
  mounted() {
    axios
      .get("https://forbes400.herokuapp.com/api/forbes400?limit=3")
      .then(({ data }) => {
        data.reverse().forEach(billionaire =>
          this.ranges.push({
            value: billionaire.finalWorth * 1000 * 1000,
            name: billionaire.person.name
          })
        );
      });
  }
};
</script>

<style lang="scss">
* {
  scroll-behavior: smooth;
}
.money-time {
  position: relative;
}
.money-time-list {
  list-style: none;
  margin: 0;
  padding: 0;
}
.money-time-navigation {
  position: fixed;
  height: 98%;
  width: 0.4em;
  background-color: pink;
  top: 1%;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  &__entry {
    height: 1em;
    width: 1em;
    border-radius: 50%;
    background-color: pink;
  }
}
</style>
