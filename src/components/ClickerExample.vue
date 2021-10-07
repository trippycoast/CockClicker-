<template>
  <section class="section">

      <button class="button is blue" @click="click++">Click it Munn!</button>
      <h4 class="heading-4">You have {{click}} clack!</h4>
      <button class="button is-warning" @click="autoClick" :disabled="clicks<cost"> auto click (0.1 clicks per second</button>
      <auto-click 
      v-for="(auto,index) in autoClickers"
      :key="index"
      name="Auto Click" 
      :cps="0.1" 
      :cost="cost" 
      :index="0" 
      :clicks="clicks"
      @clicked="autoClick">
      </auto-click>

</template>

<script>
import AutoClick from './AutoClick.vue';
export default {
  components: { AutoClick },
    data(){
        return {
            clicks: 0,
            cps: 0,
            cost: 10,
            autoclick: [

                {name: "auto click", cost: 10, cps:0.1},
                {name: "Mother", cost: 100, cps:1},
                {name: "Grandma", cost: 1000, cps:10},
                {name: "Factory", cost: 10000, cps:100},
                {name: "Step-sis", cost: 100000, cps:1000},
            ]
        }
    },
    methods: {
        autoclick(index){
            this.clicks -= this.AutoClickers[index].cost;
            this.cps += this.AutoClickers[index].cps;
            this.AutoClickers[index].cost += Math.ceil(this.AutoClickers[index].cost/7);
        }
    },
    computed: {
        displayClicks(){
            return this.clicks.toFixed(1);
        }
    }
}
</script>

<style>

</style>