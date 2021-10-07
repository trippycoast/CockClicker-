<template>
  <button class="button is-warning" @click="autoClick" :disabled="clicks<cost">
      {{name}} ({{cps}} click per second) cost: {{cost}} clicks
  </button>

</template>

<script>
export default {
    props: ["cost", "cps", "name", "cliks"],
    methods: {
        autoclick(){
            this.$emit("clicked", this.index);
        }
    }
}
</script>

<style>

</style>