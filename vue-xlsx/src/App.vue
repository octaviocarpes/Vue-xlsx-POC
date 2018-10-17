<template>
  <div id="app">
    <importXlsx :sheet="sheet"/>
    <sheetsComponent :sheet="sheet"/>
  </div>
</template>

<script>
import importXlsx from './components/ImportXlsx.vue'
import sheetsComponent from './components/SheetsComponent.vue'

export default {
  data() {
    return {
      sheet:[]
    }
  },
  name: "app",
  components: {
    importXlsx,
    sheetsComponent
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
