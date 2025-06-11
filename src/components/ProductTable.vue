<template>
  <div>
    <h2>Daftar Produk</h2>
    <table>
      <thead>
        <tr>
          <th>Produk</th>
          <th>Harga</th>
          <th>Views</th>
          <th>Status</th>
          <th>Aksi</th>
        </tr>
      </thead>
      <tbody>
        <ProductRow
          v-for="(item, index) in produkList"
          :key="index"
          v-bind="item"
          @hapus="$emit('hapus-produk', index)"
          @edit="$emit('edit-produk', index)"
        />
      </tbody>
    </table>
  </div>
</template>

<script setup>
import ProductRow from './ProductRow.vue'
defineProps(['produkList'])
defineEmits(['hapus-produk', 'edit-produk'])
</script>

<style scoped>
table {
  width: 100%;
  border-collapse: separate;
  border-spacing: 0 8px;
  background: transparent;
}

thead {
  background-color: #f3f4f6;
  color: #374151;
  font-weight: 600;
  font-size: 0.95rem;
}

th {
  padding: 0.75rem 1rem;
  text-align: left;
  font-size: 0.95rem;
}

tbody tr {
  background-color: #ffffff;
  border-radius: 8px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05);
  transition: background 0.2s ease;
}

tbody tr:hover {
  background-color: #f9fafb;
}

td {
  padding: 0.75rem 1rem;
  font-size: 0.9rem;
  color: #4b5563;
  vertical-align: middle;
}
</style>





