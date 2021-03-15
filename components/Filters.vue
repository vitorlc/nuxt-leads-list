<template>
  <div>
    <label>Nome:</label>
    <input v-model="name"/>
    <label >Categorias</label>
    <select v-model="category">
      <option 
        v-for="(option, index) in categoryOptions"
        :key="index"
        :value="option">{{option}}</option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    categoryOptions: Array
  },
  watch: {
    name: function (value) {
      this.$emit('changeName', value)
    }
  },
  data () {
    return {
      name: '',
      category: null
    }
  }
};
</script>

<style>
</style>