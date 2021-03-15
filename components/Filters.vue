<template>
  <div>
    <label>Nome:</label>
    <input v-model="filter.name" />
    <label>Categorias</label>
    <select v-model="filter.category">
      <option
        v-for="(option, index) in categoryOptions"
        :key="index"
        :value="option"
      >
        {{ option }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    categoryOptions: Array,
  },
  watch: {
    filter: {
      handler(value) {
        this.$emit("changeFilter", value);
      },
      deep: true,
    },
  },
  data() {
    return {
      filter: {
        name: "",
        category: null,
      },
    };
  },
  methods: {},
};
</script>

<style>
</style>