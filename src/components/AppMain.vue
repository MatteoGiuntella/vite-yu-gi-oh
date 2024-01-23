<script>
import { store } from "../store";
import SetCard from "./SetCard.vue";
export default {
  data() {
    return {
      store,
    };
  },
  components: {
    SetCard,
  },
  methods: {},
};
</script>

<template>
  <div class="bg-main">
    <div class="container">
      <div class="row my-3">
        <div class="col4">
          <select class="form-select my-2 " aria-label="Default select example">
            <option selected>Choose you type</option>
            <option value="1" v-for="(elem,i) in this.store.selectorCard" >{{ elem.archetype_name }}</option>
          </select>
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
