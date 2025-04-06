<script setup>
import { ref } from 'vue';

const price = ref(0);
const count = ref(0);
const date = ref('');
const total = ref(0);

function calculate() {
  total.value = price.value * count.value;
}

function resetForm() {
  price.value = 0;
  count.value = 0;
  date.value = '';
  total.value = 0;
}

function imprimir() {
  window.print();
}
</script>

<template>
  <div class="calculator-app">
    <header class="bg-black text-white py-4 mb-5 shadow">
      <div class="container">
        <h1 class="display-5 fw-bold">Calculadora</h1>
        <p class="lead mb-0">Simple calculadora usando Vue.js</p>
      </div>
    </header>

    <main class="container mb-5">
      <div class="row justify-content-center">
        <div class="col-lg-8">
          <div class="card shadow-sm border-0">
            <div class="card-header bg-light">
              <h3 class="mb-0">Datos de Cálculo</h3>
            </div>
            <div class="card-body">
              <div class="row mb-4">
                <div class="col-md-6 mb-3">
                  <label for="price" class="form-label fw-semibold">Digite el precio:</label>
                  <div class="input-group">
                    <span class="input-group-text">$</span>
                    <input 
                      id="price"
                      type="number" 
                      class="form-control" 
                      placeholder="Ingrese el precio" 
                      v-model="price"
                      @input="calculate"
                    />
                  </div>
                </div>
                <div class="col-md-6 mb-3">
                  <label for="count" class="form-label fw-semibold">Digite la cantidad:</label>
                  <input 
                    id="count"
                    type="number" 
                    class="form-control" 
                    placeholder="Ingrese la cantidad" 
                    v-model="count" 
                    @input="calculate"
                  />
                </div>
                <div class="col-md-6">
                  <label for="date" class="form-label fw-semibold">Fecha:</label>
                  <input 
                    id="date"
                    type="date" 
                    class="form-control" 
                    v-model="date"
                  />
                </div>
              </div>

              <div class="results bg-light p-4 rounded mb-4">
                <div class="row">
                  <div class="col-md-4 mb-2">
                    <div class="d-flex flex-column">
                      <span class="text-muted fs-6">Precio:</span>
                      <span class="fs-5">${{ price }}</span>
                    </div>
                  </div>
                  <div class="col-md-4 mb-2">
                    <div class="d-flex flex-column">
                      <span class="text-muted fs-6">Cantidad:</span>
                      <span class="fs-5">{{ count }}</span>
                    </div>
                  </div>
                  <div class="col-md-4 mb-2">
                    <div class="d-flex flex-column">
                      <span class="text-muted fs-6">Fecha:</span>
                      <span class="fs-5">{{ date }}</span>
                    </div>
                  </div>
                </div>
                <hr>
                <div class="d-flex justify-content-between align-items-center">
                  <span class="fw-bold fs-5">Total a pagar:</span>
                  <span class="fw-bold fs-4 text-black">${{ total }}</span>
                </div>
              </div>

              <div class="d-flex justify-content-end gap-2">
                <button @click="resetForm" type="button" class="btn btn-outline-secondary">
                  Reiniciar
                </button>
                <button @click="imprimir" type="button" class="btn btn-info">
                  <i class="bi bi-printer me-1"></i> Imprimir
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </main>

    <footer class="bg-light py-4 mt-auto">
      <div class="container text-center text-muted">
        <p class="mb-0">&copy; {{ new Date().getFullYear() }} - Calculadora Vue.js</p>
      </div>
    </footer>
  </div>
</template>

<style>
@media print {
  header, footer, button {
    display: none !important;
  }
  
  .calculator-app {
    background-color: white;
    height: 100%;
    width: 100%;
    position: fixed;
    top: 0;
    left: 0;
    margin: 0;
    padding: 15px;
  }
  
  .results {
    border: 1px solid #ddd;
  }
}

body {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

main {
  flex: 1 0 auto;
}

.calculator-app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
</style>