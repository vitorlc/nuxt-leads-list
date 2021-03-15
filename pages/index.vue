<template>
  <div class="leads">
    <Logo />
    <!-- <Logo dark-background /> -->
    <main>
      <Lead v-for="lead in leads" :key="lead.id" :lead="lead"/>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      leads: []
    }
  },
  async fetch () {
    this.leads = await fetch('https://jsonplaceholder.typicode.com/users').then(res => res.json())
  }
}
</script>

<style lang="scss" scoped="true">
.leads {
  &__title {
    margin: 1.4rem 0;
    padding: 1.4rem 0;
    border-top: $border-color 1px solid;
  }
}
</style>
