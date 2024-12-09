<template>
    <div id="list-wrapper">
    <div
      class="item"
      v-for="(item, index) in items"
      :key="index"
      @click="alternarFeito(index)"
      :class="{ importante: item.importante, feito: item.feito }"
    >
      <p class="texto-item">{{ item.texto }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "List",
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
  methods: {
    alternarFeito(index) {
      this.$emit("toggle-item", index);
    },
  },
};
</script>