<template>
  <span class="date-list-item">
    <div class="date-list-item__value">
      {{ value.toLocaleString() }} ({{ name }})
    </div>
    <div>seconds ago, was</div>
    <div class="date-list-item__date">{{ dateValue }}</div>
  </span>
</template>

<script>
export default {
  name: "DateListItem",
  props: {
    value: Number,
    name: String
  },
  computed: {
    dateValue: function() {
      return new Date(Date.now() - this.value * 1000).toLocaleDateString(
        "en-US",
        {
          day: "numeric",
          month: "long",
          year: "numeric",
          era: "short"
        }
      );
    }
  }
};
</script>

<style lang="scss" scoped>
.date-list-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 2em;
  &__value,
  &__date {
    font-size: 1.2em;
  }
}
</style>
