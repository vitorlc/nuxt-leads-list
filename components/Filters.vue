<template>
  <div class="container">
    <div class="filter">
      <label>Nome:</label>
      <input v-model="filter.name" />
    </div>
    <div class="filter">
      <label>Categorias: </label>
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
    <button @click="clearFilter" class="button_clear">Limpar</button>
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
  methods: {
    clearFilter() {
      this.filter.name = "";
      this.filter.category = null;
    },
  },
};
</script>

<style lang="scss" scoped="true">
.container {
  width: 700px;
  justify-content: space-between;
  display: flex;
  flex-wrap: wrap;
}
.filter  {
  margin-top: 5px;
}
.button_clear {
  height: 80%;
  width: 65px;
  border-radius: 10px;
  padding: 10;
  font-size: 20;
  font-weight: "bold";
  color: white;
  background-color: $dark-blue;
}
</style>