<template>
    <div class="container mt-5">
      <h2>Ventes Enregistrées</h2>
      <table class="table table-striped">
        <thead>
          <tr>
            <th>Référence</th>
            <th>Désignation</th>
            <th>Quantité</th>
            <th>Prix</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(sale, index) in sales" :key="index">
            <td>{{ sale.reference }}</td>
            <td>{{ sale.designation }}</td>
            <td>{{ sale.quantity }}</td>
            <td>{{ sale.price.toFixed(2) }}</td>
          </tr>
          <tr v-if="sales.length === 0">
            <td colspan="4" class="text-center">Aucune vente enregistrée</td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  export default {
    name: 'SalesTable',
    props: {
      sales: Array
    }
  }
  </script>
  
  <style scoped>
  /* Ajoutez des styles personnalisés ici si nécessaire */
  </style>
  