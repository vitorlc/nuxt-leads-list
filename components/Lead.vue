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
          <b> Endereço: </b> {{ transformAddress }}
        </p>
        <p>
          <b> Empresa: </b> {{lead.company.name}}
        </p>
        <div class="company_sub_itens">
          <p>
            <b> Categorias: </b> {{lead.company.bs}}
          </p>
          <p>
            <b> Palavra Chave: </b> {{lead.company.catchPhrase}}
          </p>
        </div>
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
    },
    transformAddress() {
      let address = Object.entries(this.lead.address)
      let text = ''
      for(let e of address) {
        if(typeof e[1] == 'object') continue
        text = text +` ${e[0].charAt(0).toUpperCase() + e[0].slice(1)}: ${e[1]};`
      }
      return text
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
.details p {
  padding-top: 10px
}
.company_sub_itens {
  padding-left: 10px;
}
</style>