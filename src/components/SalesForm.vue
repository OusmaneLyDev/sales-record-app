<template>
    <div class="container mt-5">
      <h2>Enregistrement des Ventes</h2>
      <form @submit.prevent="submitForm">
        <div class="mb-3">
          <label for="reference" class="form-label">Référence</label>
          <input
            type="text"
            id="reference"
            v-model="sale.reference"
            class="form-control"
            :class="{ 'is-invalid': errors.reference }"
          />
          <div class="invalid-feedback">{{ errors.reference }}</div>
        </div>
        <div class="mb-3">
          <label for="designation" class="form-label">Désignation</label>
          <input
            type="text"
            id="designation"
            v-model="sale.designation"
            class="form-control"
            :class="{ 'is-invalid': errors.designation }"
          />
          <div class="invalid-feedback">{{ errors.designation }}</div>
        </div>
        <div class="mb-3">
          <label for="quantity" class="form-label">Quantité Vendue</label>
          <input
            type="number"
            id="quantity"
            v-model="sale.quantity"
            class="form-control"
            :class="{ 'is-invalid': errors.quantity }"
          />
          <div class="invalid-feedback">{{ errors.quantity }}</div>
        </div>
        <div class="mb-3">
          <label for="price" class="form-label">Prix de Vente</label>
          <input
            type="number"
            id="price"
            v-model="sale.price"
            class="form-control"
            :class="{ 'is-invalid': errors.price }"
          />
          <div class="invalid-feedback">{{ errors.price }}</div>
        </div>
        <button type="submit" class="btn btn-primary">Enregistrer</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    name: 'SalesForm',
    data() {
      return {
        sale: {
          reference: '',
          designation: '',
          quantity: '',
          price: ''
        },
        errors: {}
      }
    },
    methods: {
      validate() {
        this.errors = {};
        let valid = true;
  
        if (!this.sale.reference) {
          this.errors.reference = 'La référence est requise.';
          valid = false;
        }
        if (!this.sale.designation) {
          this.errors.designation = 'La désignation est requise.';
          valid = false;
        }
        if (!this.sale.quantity || this.sale.quantity <= 0) {
          this.errors.quantity = 'La quantité doit être un nombre positif.';
          valid = false;
        }
        if (!this.sale.price || this.sale.price <= 0) {
          this.errors.price = 'Le prix doit être un nombre positif.';
          valid = false;
        }
  
        return valid;
      },
      submitForm() {
        if (this.validate()) {
          this.$emit('sale-added', { ...this.sale });
          this.sale = { reference: '', designation: '', quantity: '', price: '' };
          this.errors = {};
        }
      }
    }
  }
  </script>
  
  <style scoped>
  /* Ajoutez des styles personnalisés ici si nécessaire */
  </style>

