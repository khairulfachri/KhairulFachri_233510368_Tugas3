<template>
  <main class="app">
    <h1>Manajemen Produk</h1>

    <form @submit.prevent="isEditing ? updateProduk() : tambahProduk()" class="form">
      <input v-model="judul" placeholder="Nama Produk" required />
      <input v-model.number="harga" type="number" placeholder="Harga" required />
      <input v-model.number="views" type="number" placeholder="Jumlah Views" required />
      <select v-model="status">
        <option>Aktif</option>
        <option>Nonaktif</option>
      </select>
      <button type="submit">{{ isEditing ? 'Update' : 'Tambah' }} Produk</button>
      <button v-if="isEditing" type="button" @click="batalEdit">Batal</button>
    </form>

    <ProductTable
      :produkList="produkList"
      @hapus-produk="hapusProduk"
      @edit-produk="editProduk"
    />
  </main>
</template>

<script setup>
import { ref } from 'vue'
import ProductTable from './components/ProductTable.vue'

const produkList = ref([])

const judul = ref('')
const harga = ref(0)
const views = ref(0)
const status = ref('Aktif')

const isEditing = ref(false)
const editingIndex = ref(null)

function tambahProduk() {
  produkList.value.push({
    judul: judul.value,
    harga: harga.value,
    views: views.value,
    status: status.value,
  })
  resetForm()
}

function hapusProduk(index) {
  produkList.value.splice(index, 1)
  batalEdit()
}

function editProduk(index) {
  const produk = produkList.value[index]
  judul.value = produk.judul
  harga.value = produk.harga
  views.value = produk.views
  status.value = produk.status
  isEditing.value = true
  editingIndex.value = index
}

function updateProduk() {
  if (editingIndex.value !== null) {
    produkList.value[editingIndex.value] = {
      judul: judul.value,
      harga: harga.value,
      views: views.value,
      status: status.value,
    }
    batalEdit()
  }
}

function batalEdit() {
  isEditing.value = false
  editingIndex.value = null
  resetForm()
}

function resetForm() {
  judul.value = ''
  harga.value = 0
  views.value = 0
  status.value = 'Aktif'
}
</script>

<style scoped>
.app {
  max-width: 1000px;
  margin: 2rem auto;
  padding: 2rem;
  background: #ffffff;
  font-family: 'Segoe UI', sans-serif;
  border-radius: 12px;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.06);
}

h1 {
  font-size: 1.8rem;
  font-weight: bold;
  color: #2f3e4e;
  margin-bottom: 1.5rem;
  text-align: center;
}

.form {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  margin-bottom: 2rem;
  background: #f9fafb;
  padding: 1rem 1.5rem;
  border-radius: 10px;
  box-shadow: inset 0 0 0 1px #e5e7eb;
}

input, select {
  flex: 1 1 200px;
  padding: 0.6rem 0.8rem;
  border: 1px solid #d1d5db;
  border-radius: 6px;
  font-size: 0.95rem;
  background-color: #fff;
  color: #374151;
  transition: border-color 0.2s ease;
}

input:focus {
  border-color: #10b981;
  box-shadow: 0 0 0 1px #10b981;
  outline: none;
}

button[type="submit"] {
  background-color: #10b981;
  color: white;
  border: none;
  font-weight: 600;
  padding: 0.6rem 1.2rem;
  border-radius: 6px;
  cursor: pointer;
  transition: background 0.2s ease;
}

button[type="submit"]:hover {
  background-color: #059669;
}
</style>

