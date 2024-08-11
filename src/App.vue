<template>
  <div id="app">
    <SalesForm @sale-added="addSale"/>
    <SalesTable :sales="sales"/>
  </div>
</template>

<script>
import SalesForm from './components/SalesForm.vue'
import SalesTable from './components/SalesTable.vue'

export default {
  name: 'App',
  components: {
    SalesForm,
    SalesTable
  },
  data() {
    return {
      sales: []
    }
  },
  methods: {
    addSale(sale) {
      this.sales.push(sale);
    }
  }
}
</script>

<style>
/* Ajoutez des styles globaux ici si nécessaire */
</style>
