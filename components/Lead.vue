<template>
  <div class="card">
    <div class="card_header">
      <div>
        <h3 class="card_title">{{ lead.name }}</h3>
        <p class="card_title">{{ lead.phone }} ‧ {{ lead.email }} ‧ {{ lead.website }}</p>
      </div>
      <div class="card_information" >
        <div class="arrow" :style="arrowStyle" @click="showDetails = !showDetails"></div>
      </div>
    </div>
    <div v-if="showDetails" class="details">
      <hr>
      <p>
        Teste
      </p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    lead: Object,
  },
  computed: {
    arrowStyle () {
      return { 
        transform: !this.showDetails ? 'rotate(225deg)' : 'rotate(45deg)',
        'transition-duration': '0.5s'
      }
    }
  },
  data() {
    return {
      showDetails: false
    }
  }
};
</script>

<style lang="scss" scoped="true">
.card {
  background-color: white;
  border-radius: 10px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  transition: 0.3s;
  padding: 15px;
  margin-bottom: 10px;
}
.card_header {
  justify-content: space-between;
  display: flex;
  flex-wrap: wrap;
  
}
.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
}
.card_title {
  padding-bottom: 5px;
}
.arrow {
  margin: 10px;
  width: 12px;
  height: 12px;
  border-top: 2px solid $dark-blue;
  border-left: 2px solid $dark-blue;
}
.card_information {
  flex-direction: row;
}
.card_information:hover {
  transform: translate3d(0, 5px, 0);
}
hr { 
  border-color: $dark-blue 
}
</style>