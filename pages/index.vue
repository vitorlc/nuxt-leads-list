<template>
  <div class="leads">
    <Logo />
    <!-- <Logo dark-background /> -->
    <div class="row">
      <h1>Leads</h1>
      <Filters
        :categoryOptions="categoryOptions"
        @changeFilter="changeFilter"
      />
    </div>
    <main>
      <Lead v-for="lead in leadsFiltered" :key="lead.id" :lead="lead" />
    </main>
  </div>
</template>

<script>
export default {
  computed: {
    leadsFiltered() {
      return this.leads.filter((e) => {
        if (e.name.toLowerCase().indexOf(this.filter.name.toLowerCase()) === -1 ||
        (this.filter.category && e.company.bs !== this.filter.category))
          return false
        return true
      });
    },
  },
  data() {
    return {
      leads: [],
      categoryOptions: [],
      filter: {
        name: "",
        category: null,
      },
    };
  },
  async fetch() {
    this.leads = await fetch(
      "https://jsonplaceholder.typicode.com/users"
    ).then((res) => res.json());
    this.leads.forEach((e) => this.categoryOptions.push(e.company.bs));
  },
  methods: {
    changeFilter(value) {
      this.filter = value
    }
  }
};
</script>

<style lang="scss" scoped="true">
.row {
  margin: 1.4rem 0;
  padding: 1.4rem 0;
  border-top: $border-color 1px solid;
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
  justify-content: space-between;
  margin: 1.4rem 0;
  padding: 1.4rem 0;
}
</style>
