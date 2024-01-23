<script>
import { store } from "../store";
import SetCard from "./SetCard.vue";
import axios from 'axios';
export default {
  data() {
    return {
      store,
      utentSelect : ''
    };
  },
  components: {
    SetCard,
  },
  methods: {
      utentType (){
        axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0',{
            params:{
              archetype : this.utentSelect,
            }}).then((response)=>{
              this.store.listCard = response.data.data
            })
            
      }
  },
};
</script>

<template>
  <div class="bg-main">
    <div class="container">
      <div class="row my-3">
        <div class="col4">
          <select v-model="utentSelect" class="form-select my-2 " aria-label="Default select example">
            <option selected>Search</option>
            <option :value="elem.archetype_name" v-for="(elem,i) in this.store.selectorCard" >{{ elem.archetype_name }}</option>
          </select>
          <button @click="utentType" type="button" class="btn btn-danger">Ricerca</button>
        </div>
      </div>
      <div class="row my-2">
        <div class="col-12">
          <div class="founded-card bg-black p-2">
            <h4 class="text-light">foundes {{ store.listCard.length }}</h4>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-2" v-for="(elem, i) in this.store.listCard">
          <SetCard :singlecard="elem" />
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
div {
  background-color: orange;
}
</style>
